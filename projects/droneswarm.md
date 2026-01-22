---
layout: project
type: project
image: img/modalai-inc-drone-px4-autonomy-developer-kit-43777518207280_2000x.jpg
title: "Drone Swarm Investigation"
date: 2025
published: true
labels:
  - Ubuntu
  - Python
summary: "An autonomous drone swarm that collects environmental data, processes it collaboratively, and executes real-time response actions."
---

<img class="img-fluid" src="../projects/firesimulation.png">

Drone security is versatile because multiple drones can work together to cover large areas more efficiently. Our team and I, Hoverlogic, simulated a team of drones that shared what each one detected and automatically spread out to monitor a wildfire simulation. Using an ArduPilot-based system, we relied on a shared gossip bus that gives input to the other drones so they can be assigned their own roles. The rules that we implemented are random walk and assigned patterns. 

The following Code represents a snapshot of the wildfire image shown above: 

'''
def fire_snapshot(self, t_now: float) -> Tuple[int,int,float,float]:
    burn = 0
    burnt = 0
    total = self.N * self.N
    for i in range(self.N):
        for j in range(self.N):
            s = self.fire_state[i][j]
            if s == 1:
              burn += 1
            elif s == 2:
              burnt += 1
    burn_frac = burn / total
    burnt_frac = burnt / total
    detected = self.fire_detections()
    self.fire_ts.append((t_now, burn, burnt, burn_frac, burnt_frac, detected))
    return burn, burnt, burn_frac, burnt_frac, detected


'''


