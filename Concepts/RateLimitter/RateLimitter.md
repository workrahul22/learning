Rate Limitting/Throttling

Why use rate limitter?
    1. To Prevent Denial of Service Attack

How to design a rate limitter?

    Functional Requirements?
        1. We limit the number of request can make to an API in a given time.
        
    Non Functional Requirements?
        1. what kind of rate limiter are we building?
            clien-side
            middleware
            server-side

Where to store the counter?
    1. in memory
    2. cache(redis)
    3. database(mysql)


Rate Limitter Algorithms

1. Leaking Bucket Algorithm
    if the bucket is full then it will not allow any more request
    at a regular interval the request gets pulled from the bucket and this will make space for new request

        Bicket size : The number of max request wait in the queue
        Process Rate: how many request can be retreated in a second

        Pros:
            memory efficient
            stable processing rate
        cons:
            weak support for burst traffic
            parameters difficult to get right
2. Token Bucket Algorithm
    same like leaking buket algorithm
    lets say we have bucket with predefined capacity
    then we add tokens to the bucket at preodic moment of time
    this bucket can store token untill it gets fulled
    when some request come then it will consume one token each
    if bucket is empty then new request will be dropped

    it takes 2 parameters
        1. bucket size
        2. Refil Rate: Rate at which the token gets added perodically

    How many buckets we need.

    Pro:
        memory efficient
        allow bursts of traffic for short periods
    cons
        parameter difficult to get right

3. Fixed Window Algorithm
    
4. Sliding Window Counter Algorithms
5. Sliding Window Log Algorithm
