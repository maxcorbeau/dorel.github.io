---
layout: manual
title: Designing a scalable solution
category: Analytics
draft: false
---

## The wrong way ##

As an example, let's consider the following Analytics implementation based on Google Analytics (GA) and Google Tag Manager (GTM):

![Example GA/GTM process](/assets/img/analytics/process_ga_gtm.png)

If no efforts are made to design a unified process from end to end, what happens is that at each step of the process, business units will deploy resources to satisfy their own needs only, causing duplication, and pass those down to the next step, where business units will repeat the same approach. Ultimately the analytics process looks as follows: 

![Process branching out](/assets/img/analytics/process_ga_gtm_wrong_branching.png)

As the core of the problem might not be fully obvious from such a representation, it is important to understand that what we face in that case is an exponential growth of complexity as the company scales

![Exponentially growing complexity](/assets/img/analytics/complexity_exponential.png)

## The right way ##

Following the initial example, what one should achieve is a design whereby business units share common analytics resources throughout the process, for as long as reasonably possible, and where only start deploying resources to address their specific needs as late as possible, ideally at the last step: reporting.

![Process Simplification](/assets/img/analytics/process_ga_gtm_simplification.png)

The goal being obviously to deliver a scalable Analytics as a Service, whereby complexity does not growh as the organization does:

![Flat complexity](/assets/img/analytics/complexity_flat.png)

This is obviously a dream scenario and not realistic given the fact that:

 - it is impossible to anticipate on all future needs: 
 - as technology progresses, the business will want to deploy new solutions to improve reporting capabilities

So in practice the flat line never happens, but at least it shouldn't grow exponentially:

![Flat complexity](/assets/img/analytics/complexity_realistic.png)

### Principles ###

Accordingly, here are the principles we must follow to design an analytics solution that can scale:

 - Design generic & flexible
 - Re-use whenever possible
 - Avoid duplication
 - If you have to duplicate, do it as late as possible (ideally at reporting level)