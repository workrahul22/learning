# Stress testing assesses how the system performs when loads are heavier than usual.

### The load pattern of a stress test resembles that of an average-load test. The main difference is higher load. To account for higher load, the ramp-up period takes longer in production to the load increase. Similiarly, after the test reaches the desired loca, it might last for slightly longer than in the average-load test.

### image

### In some testing conversation, stress test might also be called rush-hour, surge, or scale tests.

## When to perform a stress test

### stress tests verify that stability and reliability of the system under conditions of heavy use. Systems may receive higher than usual workloads on unusual moments such as process deadlines, paydays, rush hours, ends of the workweek, and many other behaviors that might cause frequent higher-than-average traffic.

### Consideration

1. Load should be higher than what the system experiences on average.
    some testers might have default targets for stress tests-say an increase upon average load by 50 or 100 percent there's no fixed percentage.
    The load simulated in a stress test depends on the stressful situations that the system may be subject to. sometimes this may be just a few percentage points above that average. Other times, it can be 50 to 100% higher, as mentioned. Some stressful situations can be twice, triple, or even orders of magnitude higher.
    Define load according to the risk oad patterns that the system may receive.
2. Only run stress tests after running average-load tests.
    Identify performance issues under average-load tests before trying anything more challenging. this sequence is essential.
3. Re-use the averageload test script.
    Modify the paremeters to have higher load or VUs
4. Expect worse performance compared to average load.
    The test determines how much the performance degrades with the extra load and whether the system survives it. A wellperformant system should respond with consistent response times when handling a constant workload for an extended period.
