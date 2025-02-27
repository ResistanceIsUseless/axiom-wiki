Spinning up and managing individual instances is easy, however, what about several instances?

A bunch of instances, usually an odd number, 3 or greater, is known as a fleet. A fleet consists of a set of hosts, these can be used for parallel file transfers, scans, or parallel command execution

### Starting a fleet
```
axiom-fleet <fleet> -i=<number of instances> 
axiom-fleet jarvis -i=5
```

The above command will start a fleet called "jarvis" with 5 instances. Automatic shutdown of droplets has been deprecated, we noticed it was mostly unused and added more complexity than it paid off. If you want to see a return of automatic disposal - please make an issue!

### List instances
List your new running instances:
```
axiom-ls
```

### Select your instances
To use your instances in parallel activities, you need to select them:
```
axiom-select 'jarvis*'
```

This will remember what instances are in your fleet, and put these in a temporary cache file in `~/.axiom/selected.conf`

### Execute a command on every instance
```
axiom-exec 'ifconfig eth0'
```

The above command will run this command on all instances, watch as you can concurrently execute single tasks. 

### Execute a command in the background on every instance
```
axiom-execb 'ifconfig eth0'
```

### Upload a file to all instances in a fleet
```
axiom-scp 'wordlist.txt' 'jarvis*':'~/wordlist.txt'
```

This will in parallel upload the wordlist, this can be done for both uploads and downloads.

