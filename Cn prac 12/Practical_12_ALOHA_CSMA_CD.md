# Practical 12: ALOHA and CSMA/CD Using a Simulator

## Aim
To study the functioning of ALOHA and CSMA/CD using a network simulator such as NS2.

> **Important:** The scripts below are simplified Tcl teaching models. They demonstrate overlapping transmissions and channel sensing, but they are **not complete NS2 MAC-layer implementations**. The CSMA/CD model does not implement actual collision detection, jam signals, or binary exponential backoff.

## Step 1: Open the Terminal

Open Terminal on the Linux PC using `Ctrl + Alt + T`.

Check whether NS2 is installed:

```bash
ns
```

At the `%` prompt, enter:

```tcl
puts "NS2 is working"
exit
```

If `NS2 is working` appears, continue.

## Step 2: Install the Required Packages

If NS2, NAM, or nano is not installed, run:

```bash
sudo apt update
sudo apt install ns2 nam nano
```

If the packages are already installed, skip this step.

## Step 3: Create a Folder

```bash
mkdir -p ~/CN_Practical12
cd ~/CN_Practical12
```

## Step 4: Create the ALOHA Script

Open the editor:

```bash
nano aloha.tcl
```

Paste this code:

```tcl
# Simplified Pure ALOHA teaching model
set txTime 0.10
set starts {0.00 0.05 0.10 0.30 0.45 0.50 0.70 0.90}

set total [llength $starts]
set success 0
set collision 0

puts "PURE ALOHA SIMULATION"
puts "---------------------"

for {set i 0} {$i < $total} {incr i} {
    set start [lindex $starts $i]
    set end [expr {$start + $txTime}]
    set collided 0

    for {set j 0} {$j < $total} {incr j} {
        if {$i == $j} {
            continue
        }

        set otherStart [lindex $starts $j]
        set otherEnd [expr {$otherStart + $txTime}]

        if {$start < $otherEnd && $otherStart < $end} {
            set collided 1
            break
        }
    }

    if {$collided} {
        incr collision
        puts "Packet [expr {$i+1}]: COLLISION"
    } else {
        incr success
        puts "Packet [expr {$i+1}]: SUCCESS"
    }
}

puts "---------------------"
puts "Packets attempted: $total"
puts "Successful packets: $success"
puts "Packets affected by collisions: $collision"
```

Save and exit nano:

1. Press `Ctrl + O`.
2. Press `Enter`.
3. Press `Ctrl + X`.

## Step 5: Run the ALOHA Model

```bash
ns aloha.tcl
```

The output identifies transmissions that overlap and those that succeed. This teaching model does not generate an NS2 packet trace or NAM animation.

## Step 6: Create the CSMA/CD Concept Model

Open a new file:

```bash
nano csma_cd.tcl
```

Paste this code:

```tcl
# Simplified CSMA/CD teaching model
set txTime 0.10
set requests {0.00 0.05 0.10 0.30 0.45 0.50 0.70 0.90}

set total [llength $requests]
set success 0
set retries 0
set channelFreeAt 0.0

puts "CSMA/CD CONCEPT MODEL"
puts "---------------------"

for {set i 0} {$i < $total} {incr i} {
    set request [lindex $requests $i]

    if {$request < $channelFreeAt} {
        set retries [expr {$retries + 1}]
        set request $channelFreeAt
        puts "Packet [expr {$i+1}]: CHANNEL BUSY, waits"
    } else {
        puts "Packet [expr {$i+1}]: CHANNEL IDLE"
    }

    set channelFreeAt [expr {$request + $txTime}]
    incr success
    puts "Packet [expr {$i+1}]: TRANSMITTED"
}

puts "---------------------"
puts "Packets requested: $total"
puts "Packets transmitted in this model: $success"
puts "Requests delayed by busy channel: $retries"
puts "Note: This is not a full Ethernet collision-detection model."
```

Save and exit nano:

1. Press `Ctrl + O`.
2. Press `Enter`.
3. Press `Ctrl + X`.

## Step 7: Run the CSMA/CD Model

```bash
ns csma_cd.tcl
```

The terminal displays channel-busy, waiting, and transmission messages. This model demonstrates channel sensing and waiting, but it does not implement actual collision detection, jam signals, or binary exponential backoff.

## Step 8: Record the Observations

Record the output actually produced by each script. Do not claim NAM animation, packet delivery ratios, or real NS2 MAC-layer results from these scripts.

| Feature | Pure ALOHA teaching model | CSMA/CD concept model |
|---|---|---|
| Channel sensing | No | Yes |
| Overlapping transmissions | Can collide | Requests wait when the channel is busy |
| Collision detection | Simplified overlap check | Not implemented |
| Output | Success/collision labels | Busy-channel/wait labels |

## Result / Conclusion

The experiment demonstrates the basic difference between ALOHA and carrier-sensing access. ALOHA permits transmissions without first checking whether the channel is free, so overlapping transmissions can collide. Carrier sensing allows a station to wait when the channel is busy. A complete CSMA/CD implementation additionally requires collision detection and retransmission behavior.

## Note for the College Practical

If the instructor expects genuine NS2 simulation files and NAM screenshots, these two teaching scripts are not sufficient. Use a verified MAC-layer implementation supplied by the lab or instructor, then run it using `ns filename.tcl` and inspect the generated trace and animation files.
