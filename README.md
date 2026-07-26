# *Hello!*

I'm Jacob, an early-career software engineer. My background is in web and mobile app development (React, Vue, Node.js, AWS/GCP), but lately I've been pointing that experience at a much lower-level problem: real spacecraft flight software.

## [cFS Spacecraft Docking Simulator](https://github.com/JayyCub/cFS_Project)

A hardware-in-the-loop docking simulator built on **NASA's Core Flight System (cFS)** — the same flight software framework NASA uses on real missions. A Unity physics engine simulates a chaser vehicle in low Earth orbit; a custom C flight software application running inside cFS computes the guidance, navigation, and control (GNC) logic; the two talk over UDP in real time, just like a flight computer talking to spacecraft sensors and thrusters.

It's a learning project, but every design decision is made to mirror how real rendezvous and proximity operations (RPOD) software works — the kind that flies on SpaceX Dragon, Boeing Starliner, and NASA Orion.

![ISS approach camera — Dragon on approach with RCS plumes](https://raw.githubusercontent.com/JayyCub/cFS_Project/main/Docs/Unity_Scene_img5.png)

<p align="center">
  <img src="https://raw.githubusercontent.com/JayyCub/cFS_Project/main/Docs/Utility_UI_Approach_3m.png" width="49%" alt="Utility UI — final approach, 2.91m range" />
  <img src="https://raw.githubusercontent.com/JayyCub/cFS_Project/main/Docs/Utility_UI_Docked.png" width="49%" alt="Utility UI — DOCKED" />
</p>

**Highlights:**
- A `gnc_app` cFS application with a Dragon-style phase state machine (`IDLE` → `CORRECT` → `APPROACH` → `HOLD` → `DOCKED`), autonomous hold points, and a proportional timed-burn control law
- Clohessy-Wiltshire orbital dynamics driving realistic relative-motion drift in Unity
- A 16-thruster RCS model with a pseudo-inverse control allocator mapping 6-DOF wrench commands onto real thruster geometry
- CCSDS ground commanding, `CFE_TBL` in-flight parameter uplink, and autonomous abort monitoring via cFS's Limit Checker — all built on unmodified NASA cFS/cFE

**Stack:** C (cFS flight software) · C# (Unity 6 physics/telemetry) · Python (ground command tool) · Docker (build/runtime environment)

Check out the [full write-up and architecture diagrams](https://github.com/JayyCub/cFS_Project) for the details, or the [build journal](https://github.com/JayyCub/cFS_Project#journal) for progress screenshots along the way.

## What I'm currently focusing on learning/improving
- Flight software architecture and real-time embedded systems
- Orbital mechanics and GNC control theory
- Automation and CI/CD tooling
