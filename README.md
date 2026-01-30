# DIY-amplifier
Custom class-d amplifier board.
<img width="826" height="507" alt="image" src="https://github.com/user-attachments/assets/ca5e5287-91af-435e-ae54-7447ffe52d2d" />
This board is a Class - D audio amplifier with analog input and gain setting.
It can work with 4-16 ohm speaker on output, and supply voltage < 35V. has OCP latch and a glass fuse.

It uses 4 MOSFETS in an H-bridge configuration, allowing for BTL output and thus higher power from lower supply voltage. 
The main part is the HIP-4081A H-bridge MOSFET gate driver. It can reliably drive the MOSFETS in the hundreds of kHz switching speed.
<img width="738" height="597" alt="image" src="https://github.com/user-attachments/assets/1b2c1b05-e141-46f2-bb19-3a5b730195d1" />

The onboard discrete oscillator should be around 200kHz. The design for the oscillator came from SineLab, and i improved some parts to fit my design.
It uses a pnp constant current source connected to a capacitor, and a MOSFET to discharge the capacitor quickly to generate a Ramp wave.
The MOSFET has 0.7nC gate charge, so the TLV3501 can reliably drive it with its output current capability. 
<img width="831" height="641" alt="image" src="https://github.com/user-attachments/assets/958903a5-3f3a-4cb5-9044-689871ce6399" />

The overcurrent protection shuts off all MOSFETS when triggered, and keeps them off until the button is pressed. 
It uses an npn-pnp SCR based design to output a constant signal with a single pulse.
<img width="1052" height="605" alt="image" src="https://github.com/user-attachments/assets/b6fd5d47-80e6-45e7-aae0-930c10ce812b" />

The pwm modulation is made possible by the MCP6561 comparator. 
<img width="1218" height="509" alt="image" src="https://github.com/user-attachments/assets/707f26f8-3163-497c-be15-4b5811f26866" />

To keep voltage levels for the audio and ramp wave similar, I'm using a 2V DC bias on audio, since the ramp wave is 0-4V
<img width="1216" height="603" alt="image" src="https://github.com/user-attachments/assets/f91daf61-0361-4ad0-b4fa-43825724504a" />

The logic circuits are powered by 7812 and 7805 repectively. 
I used many caps between VCC and GND to keep noise low from the H-bridge
<img width="1416" height="710" alt="image" src="https://github.com/user-attachments/assets/062382a5-9566-4680-87fd-dc36c8946cd1" />
