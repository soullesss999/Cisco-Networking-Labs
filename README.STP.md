## Rapid PVST+ Configuration and Convergence Testing

### Objective
Configure Rapid PVST+ on all three switches and observe how the network responds when a Root Port fails. The aim was to understand how Rapid PVST+ provides faster Layer 2 convergence using alternate paths.

###Topology
<img width="1014" height="687" alt="image" src="https://github.com/user-attachments/assets/b6a3f45f-60f9-484d-9d78-ccad6bf82a12" />

### Configuration

Configured Rapid PVST+ on Switch0, Switch1 and Switch2.
<img width="1919" height="954" alt="image" src="https://github.com/user-attachments/assets/dad7e40c-1cf6-4bbc-8a33-d5807555be32" />




### Rapid PVST+ Convergence Test

I tested Rapid PVST+ by manually shutting down the Root Port on Switch2.

```cisco
configure terminal
interface fa0/1
shutdown
end
```

The interface name should be replaced with the actual Root Port used in the topology.

**Observed behaviour:**

1. Before the failure, Switch2 had a Root Port in the Forwarding state and an Alternate Port in the Discarding state.
2. I manually shut down the Root Port.
3. The Alternate Port transitioned to the Root Port role.
4. The new Root Port entered the Forwarding state.
5. Switch2 maintained connectivity to the existing Root Bridge through the alternative path.

### Verification Commands

```cisco
show spanning-tree vlan 10
show spanning-tree summary
show interfaces status
```

### Key Learnings

- Rapid PVST+ is Cisco's per-VLAN implementation of Rapid Spanning Tree Protocol (RSTP).
- Each VLAN has its own spanning-tree instance and Root Bridge election.
- The Root Bridge is a switch, whereas the Root Port is an interface on a non-root switch.
- An Alternate Port provides a backup path towards the Root Bridge.
- When a Root Port fails, an eligible Alternate Port can rapidly transition to the Root Port role.
- A new Root Bridge election is not necessary when the existing Root Bridge remains reachable.
- STP selects the best available path based on cumulative path cost and tie-breaking rules.

### Conclusion

Successfully configured Rapid PVST+ across three switches and tested its convergence behaviour by shutting down a Root Port. The experiment demonstrated how an Alternate Port can take over as the new Root Port, helping maintain connectivity without requiring a new Root Bridge election.
