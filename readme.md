# NixOS Rollo Thermal Printer Driver

Tested on Raspberry Pi 2 Model B

Sourced from https://rollo-main.b-cdn.net/driver-dl/beta/rollo-driver-raspberrypi-beta.zip

To include in `configuration.nix`:

```
services.printing.drivers = [
  (pkgs.callPackage ./rollo-driver.nix {})
];
...
hardware.printers = {
  ensurePrinters = [
    {
      name = "Rollo_LabelPrinter";
      location = "Office";
      deviceUri = "usb://Printer/ThermalPrinter?serial=AAAAAAAAAAA";
      model = "rollo/rollo-thermal.ppd";
    }
  ];
};
```

Find proper deviceUri by manually adding printer in web GUI first, then delete before `nixos-rebuild`.
