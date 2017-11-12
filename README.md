There's a Bluetooth RGB LED bulb + combined Bluetooth speaker which
identifies itself in BT scan as "Chsmartbulb".

There're many BT speaker bulbs on market, even cheaper than this, but:

* Majority are advertized as BT 2.x or 3.x.
* On a closer look, many such bulbs are actually just Bluetooth speakers,
  bulb color is not controlled via BT (and thus smartphone), insead
  there's a standalone remote (usually an IR one).

"Chsmartbulb" was bot specifically on a promise to be BT 4, and having
a smartphone app.

On arrival, an inspection showed:

1. The bulb is indeed BT 4, specifically controller inside supports
   dual mode BT EDR/BLE.
2. Despite that, the bulb color is controlled (by the app) using BT EDR,
   not BLE, specifically SPP service. (Speaker works over AVDTP (maybe A2DP)
   BT EDR only service as expected).
3. There are some BLE services are exposed, but as mentioned, the official
   app doesn't access them. The also look dummy: service UUIDs like 0x6666,
   0x7777. The first has characteristic 0x8888, reading as array of bunch of
   0x88 values, being written, it retains written value. The second has
   characteristic 0x8877, consisting of 0x77 with the similar behavior.
4. Manufacturer is "CUBE TECHNOLOGIES" (0x03EE).

The repo contains BT communication capture on Android phone, from enabling
BT to connecting to bulb, changing colors among the main ones (red, green,
blue, turning bulb on and off).

There's a script which sends sequences from the capture to bulb, but color
changing doesn't work.
