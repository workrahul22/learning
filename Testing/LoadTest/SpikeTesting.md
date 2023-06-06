##  A Spike test verifies whether the system survives and performs under sudden and massive rushes of utilization. It is one of the least common tests.

## Spike testst are useful when the systesm may experience events of sudden and massive traffic. Examples sof such events includes ticket sales, product launches, sale announcements, process deadlines, and seasonal sales.

## Spike testing increases to extremely high loads ina very short of not-existent ramp-up time. Usually, it has no plateau period or is very brief, as real users generally do not stick around doing extra steps in these situations. In the same way, the ramp-down is very fast or non-existent, letting the process iterate only once.

## Occasionally, teams should revamp the system to allow or prioritize resources for the high-demand processes during the event.

## Spike testing is the least frequent test type. The test must be executed when the system expects to receive a sudden rush of activity, which is not a commong behaviour on most platforms.

## When the system expects this type of behaviour, the spike test helps identify how the system will behave and if it will survive the sudden rush of load. The load is considerably abouve the average and frequently focuses on a different set of processes than the other test types.

## When preparing for a spike test, consider the following:

* Focus on key processes in the test type.
* The test often won't finish: Errors are common under these scenarios
* Run, tune, repeat: When your system is at risk events, the team must run spikes test and tune the system several times.
* Monitor: Backend monitoring is a must for a successful outcomes of this test.

stages : [
    {duration: "2m" target: 2000},
    {duration: "1m" target: 0}
]

# some performance metrics to assess in spike tests include pod speeds, recovery times after the load rush, time to return to normal, or the behavior on crucial system processes during the overload.

# Finding how the system responds (if it survives) to the sudden rush helps to optimize it to guarantee that it can perform during a real event. Often the load is so high that the whole system may have to be optimized to deal with the key processes. In these cases, repeat the teat until the system confidence is high.