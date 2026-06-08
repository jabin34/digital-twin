# Space Intelligence Digital Twin

A browser-based digital twin of my room. I built this to explore how a simple 3D scan combined with live environmental data and basic decision-making logic could work together in one interface.

**Live Demo:** https://harmonious-raindrop-f4e390.netlify.app/

---

## What I Built

**3D Room Scan**
I scanned my room using Polycam's Gaussian Splatting feature on my phone. The quality isn't perfect — lighting and surface texture affect how well the splat renders — but it's navigable in the browser and gives a real spatial reference for where the sensor overlays sit. Gaussian Splatting (Kerbl et al., 2023) is a newer technique for turning photo captures into 3D scenes, and Polycam makes it accessible without specialist equipment.

**Live Sensor Overlays**
Five data points update every second, floating over the 3D scene:

| Sensor | What it shows |
|---|---|
| Occupancy | How many people are in the room |
| Temperature | Indoor temperature in °C |
| CO₂ | Air quality in ppm |
| Active Devices | Number of powered devices |
| Engagement Score | A derived productivity estimate |

The values are simulated, but they're connected to each other — more people means more CO₂ and higher temperature, which drags down the engagement score. That chain reflects how indoor environments actually behave (Satish et al., 2012; Wargocki et al., 2000).

The sensor badges are positioned approximately over relevant zones in the scene. In a production system these would be anchored to real sensor locations using spatial coordinates.

**Decision Layer**
A simple rule engine watches the sensor values and surfaces recommendations when something needs attention — open a window if CO₂ gets too high, consider cooling if temperature climbs, power down devices if the room is nearly empty. Each alert explains why it fired.

---

## Why I Made This

CO₂ above 1,000 ppm is enough to measurably reduce how well people make decisions (Satish et al., 2012). Most people have no idea what the air in their room is doing. A digital twin — even a lightweight one like this — gives you that awareness in one place and tells you what to act on.

The same idea scales up. Co-working spaces, small offices, shared study rooms — any space manager could use this kind of setup for automated environmental monitoring without expensive infrastructure.

---

## Prototype Scope and Limitations

This is a proof-of-concept. A few things are worth being upfront about:

**Simulated sensors** — All environmental data is generated in the browser using a causal model rather than real hardware. This is appropriate at a prototype stage and the screening brief explicitly allows it. The simulation uses realistic interdependencies (occupancy drives CO₂ and temperature, which together affect engagement) rather than independent random values.

**Approximate badge positions** — Sensor overlays are placed visually over the scene, not anchored to real spatial coordinates. In a deployed system, each badge would be tied to the physical location of its sensor using 3D scene metadata.

**3D scan quality** — The Gaussian Splat was captured on a phone in imperfect lighting conditions. Better results would come from slower capture, more consistent lighting, and more frame overlap. LiDAR-assisted capture would improve geometry accuracy significantly.

**Next steps toward a real system** — Replace simulated values with a cheap IoT sensor stack (CO₂ module, temperature/humidity sensor), anchor badges to real spatial coordinates, and hook the decision layer into an HVAC or notification system.

---

## Stack

Plain HTML, CSS, and JavaScript — no frameworks, no backend. The 3D scene runs via Polycam's embed. Everything else runs in the browser.

---

## References

- Satish et al. (2012). Is CO₂ an indoor pollutant? *Environmental Health Perspectives, 120*(12).
- Wargocki et al. (2000). Perceived air quality and productivity in an office. *Indoor Air, 9*(3).
- Kerbl et al. (2023). 3D Gaussian splatting for real-time radiance field rendering. *ACM Transactions on Graphics, 42*(4).
- Grieves & Vickers (2017). Digital twin: Mitigating unpredictable emergent behavior. *Transdisciplinary Perspectives on Complex Systems.* Springer.