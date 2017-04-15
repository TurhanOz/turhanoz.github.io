Some time ago \(end of 2015\), I created an open source project called[RxGoogleAuthentication](https://github.com/TurhanOz/RxGoogleAuthentication)that aims to easily get an authentication token for the Google Apis, based on OAuth2 protocol.

As all of my open source project, I never ship a code without a certain quality, and that includes proper unit testing. Shipping a project without at least that, is a lack of responsibility I think. From my point of view, a developper should be responsible of producing good code quality, or at least trying to do so. Moreover, your code could now be integrated by others on their own projects, so this is all the more important that some quality is there.

# Shadows ?

To do my Unit Testing, as most of android developers, I use the Robolectric framework. I won’t get into the benefit of this framework, so you can have a look at their[landing pages](http://robolectric.org/), but the absolute crucial one for me is that it runs on the jvm, outside the emulator. The downside of that is that you don’t have the entire Android environment which you can’t use, which is problematic in some cases.

Indeed, your tests can require to rely upon the behavior of Android components that are not available as the Android OS is not there.

To compensate that, Robolectric gave you the ability to extend the behavior of Android classes and expose them into the testing environment. These extensions of classes are called « Shadows » .

As you can read on the[documentation](http://robolectric.org/extending/), _"When an Android class is instantiated, Robolectric looks for a corresponding shadow class, and if it finds one it creates a shadow object to associate with it. Every time a method is invoked on an Android class, Robolectric ensures that the shadow class' corresponding method is invoked first \(if there is one\)"_

This is really powerful in a way that you can control the behavior of a Shadow Class and also add missing Shadows.

# Concrete use case 

The open source project introduced at the beginning of this article is using the [GoogleAuthUtil](https://developers.google.com/android/reference/com/google/android/gms/auth/GoogleAuthUtil)class, and more specifically the getToken\(\) methods.

At the time I did that shadow, Robolectric didn’t have it. But it seems to have[added it](https://github.com/robolectric/robolectric/blob/master/robolectric-shadows/shadows-play-services/src/main/java/org/robolectric/shadows/gms/ShadowGoogleAuthUtil.java) 5 days ago, before writing this article.

Anyway, let’s get into the entire process of creating this shadow in concrete and practical term so this would be a great learning case.

## \#1 Create the shadow class

To create our shadow, the convention is to prefix_"Shadow"_term to our class name, in our case our shadow would be ShadowGoogleAuthUtil.

The shadow class  should be annotated with the_**@Implements**_annotation whereas the methods should be annotated with the_**@Implementation**_annotation.

In our precise case, the getToken\(\) methods of our shadow class will return a simple token string, without caring of the internal behaviour of what the authentic GoogleAuthUtil would have done. What matters to us is the output, namely having a token string.

```
@Implements(GoogleAuthUtil.class)
public class ShadowGoogleAuthUtil{

    @Implementation
    @Deprecated
    public static String getToken(Context context, String accountName, String scope) throws IOException, UserRecoverableAuthException, GoogleAuthException {
        return "token";
    }

    @Implementation
    public static String getToken(Context context, Account account, String scope) throws IOException, UserRecoverableAuthException, GoogleAuthException {
        return "token";
    }
}
```

  


## \#2 Create the custom runner

We have to declare, within a custom runner, the existence of our custom Shadow classes that can be used through Robolectric within the tests classes.

In our case, we have a single custom Shadow that we want to be loaded in the place of the authentic GoogleAuthUtil class.

```
public class CustomRunnerWithMoreShadows extends RobolectricGradleTestRunner {

    public CustomRunnerWithMoreShadows(Class
<
?
>
 testClass) throws InitializationError {
        super(testClass);
    }

    public InstrumentationConfiguration createClassLoaderConfig() {
        InstrumentationConfiguration.Builder builder = InstrumentationConfiguration.newBuilder();
        builder.addInstrumentedClass(GoogleAuthUtil.class.getName());
        return builder.build();
    }
}
```

  


## \#3 Use shadow class in Unit Tests

Having our shadow class and a custom runner that will load it, we can now use it very simply in our Unit Tests.

The first thing we have to do is of course declare the custom runner to use by using the_**@RunWith**_annotation.

Then, we also have to explicitly declare which shadows the class will use thanks to the_**@Config**_annotation, through the_**shadows**_parameters.

That’s it, whenever we will call GoogleAuthUtil.getToken\(\) method in our tests, the framework will call the method within the shadow class, and as a matter of fact, will return « token » 

```
@RunWith(CustomRunnerWithMoreShadows.class)
@Config(constants = BuildConfig.class, sdk = 21, shadows = {ShadowGoogleAuthUtil.class})
public class AuthTest {
    Auth sut;

    @Test
    public void shouldGetTokenFromEmail() throws Exception {
        String expectedToken = "token";
        String resultToken = GoogleAuthUtil.getToken(context, email, scope);
       
        assertEquals(expectedToken, resultToken);
    }
```

  


## Conclusion

Shadows are very powerful extensions that let you enhance the Robolectric framework by providing additional or missing behaviour to it.

However, its setting requires few steps that have to be carefully followed to be able to use your custom shadows.

Last thing is: if you are doing a custom shadow, please submit it to the Robolectric project so anybody can benefit from your investment. 

