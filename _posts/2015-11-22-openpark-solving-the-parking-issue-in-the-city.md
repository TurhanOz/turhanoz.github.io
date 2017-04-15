---
layout: post
title: "OpenPark - solving the parking issue in the city"
comments: true
---
Recently, I was the studying the Beacon technology, and more precisely the Eddystone format.

Beacons are cheap devices that could be deployed anywhere that has a meaning for your business, for the city but even more importantly, for the user. \(If you want to know more about beacons, I gave a talk at DroidconParis in november 2015, so [check out the video](https://speakerdeck.com/turhanoz/eddystone-droidcon-paris-2015)\).

I also participated at a hackathon on Intelligent Mobility early October 2015 in Bordeaux, France. There, I exposed two solutions for solving a global problem that lots of cities are facing \(regarding the Public Parking Places\).

![ITSBordeaux]({{ site.baseurl }}public/images/ITSBordeaux.jpeg){: .center-image }

I made the local news :\)

## Problem

I live in a big city, and if you are a car driver living in that kind of big city, you should probably know that it's a nightmare to find a public parking place available. We often waste a huge amount of time looking for a place, we get stressed, we pollute, we generate congestion. That should end, and for good.

## Solution \#1

Of one the solution could be to deploy and glue Beacons on the field and thus, equiped each public parking place with a beacon. The beacon would have an extra proximity sensor that could detect whether a car is parked above it or not. Thus, we could have, in real time, a network of availability places in the city.  
Based on this real time data, a simple mobile application could then drive you to the nearest public parking place in the city.  
It is a cheap investment for the city \(glue-ing a beacon on each place\) but could dramatically de-congestion the traffic.

### Cons of solution \#1

The solution \#1 is cost effective but has some limitation. Firstly, an enhanced beacon has to be designed. This enhancement requires R&D to include a power efficient proximity sensor on top of the beacon.  
Also, the beacon has to be rugged so is won't break out on the car's weight. Also, it has to be protected from weather \(snow, rain...\). So this enhanced beacon requires some technical challenges.

## Solution \#2

The solution \#1 is a good candidate for solving our issue, but requires more engineering. The idea is to find a solution that is simple and easily deployable. That's solution \#2.

Instead of deploying and glue-ing beacons on each public parking place, what about having a beacon inside each car, in the glove compartment ? This beacon would stay is the driver's car and paired with driver's smartphone. So, whenever the driver is parked and is leaving his car, his smartphone is able to detect that he is moving away from his car \(because beacon is all about range, so you can easily detect that you are in or out of the range of your beacon\).

Having this information, your smartphone knows that your car is parked now and that in this precise location, the parking place is no more available.  
Similarly, when you are getting back to your car, your smartphone will detect the beacon and then consider that you will leave the parking place. This information could then be broadcasted and anyone who is looking for a parking place in the area could be notified of that availability.

## What's next ?

I highly think that this will solve for good the issue of parking your car in any big city.  
In term of investment, the city could give away a beacon for each driver, for free. The investment is really low compared to the issue it is solving \(less pollution, less congestion, less stress, more happyness\).

If you want to be part of that adventure and make the world a better living place,[please contact me](https://twitter.com/turhanoz), I would be more than happy to have your collaboration.

