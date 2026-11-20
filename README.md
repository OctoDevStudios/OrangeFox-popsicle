# OrangeFox Recovery for Xiaomi 17 Pro Max (popsicle)

Unofficial OrangeFox Recovery **R12.0_1** for the **Xiaomi 17 Pro Max** (`popsicle`, `popsicle_global`, `popsicle_in`).

> **Status:** Unofficial Beta. Popsicle only — do not flash on pudding, pandora, or any other device.
>
> **Revision 2 — 2026-11-20:** NXP decryption hotfix. If you downloaded the first build, replace it.

This build is based on [marcmyworld's OrangeFox R12.0 for the Xiaomi 17 (Pudding)](https://xdaforums.com/t/recovery-unofficial-beta-orangefox-recovery-r12-0-pudding.4808550/).

## Downloads

See [Releases](https://github.com/OctoDevStudios/OrangeFox-popsicle/releases).

- `OrangeFox-popsicle-recovery-FUNCTIONAL.img` — fastboot image, signed with Xiaomi AVB
- `OrangeFox-popsicle-R12.0_1.zip` — installer ZIP for an existing TWRP/OrangeFox

```text
9f1f3d7fc3ff0cc639ccd5d96be7dd3dcea6ec3f103ed58869e8c8b55653c81e  OrangeFox-popsicle-recovery-FUNCTIONAL.img
788550ea79f672c304207ce4bc40463f767b8190560f3e2189e50f77db0faee6  OrangeFox-popsicle-R12.0_1.zip
```

## Installation

Bootloader must be unlocked. Unlocking wipes data.

```bash
adb reboot bootloader
fastboot flash recovery OrangeFox-popsicle-recovery-FUNCTIONAL.img
fastboot reboot recovery
```

- Tested on slot A. If the bootloader marks the slot unbootable after a failed boot: `fastboot set_active a`, then reboot recovery.
- Recovery uses the kernel from the active `boot` slot (`kernel_size=0`). Keep a bootable `boot` image.
- Flash to `recovery` only — never to `boot`.
- `fastboot boot` is not usable on this device.
- The image is signed with the Xiaomi AVB key; use the provided signed image/ZIP.

## Notes

- Beta build. Back up `recovery`, `boot`, `init_boot`, `vendor_boot`, `dtbo`, `persist`, `modem`, and `efs` before flashing.
- Formatting data uses F2FS with casefolding; metadata is wiped automatically after the data format.
- If a ROM ZIP contains `recovery.img`, flashing it will overwrite OrangeFox.

## Credits

- **marcmyworld** — [OrangeFox R12.0 for Xiaomi 17 (Pudding)](https://xdaforums.com/t/recovery-unofficial-beta-orangefox-recovery-r12-0-pudding.4808550/) — base recovery, device tree and thread
- TeamWin — TWRP
- OrangeFox Team
- YuKongA — TWRP `sm8850` base trees
- antocorvo3000 — TWRP popsicle base and `se_omapi`
- KernelSU / KernelSU-Next / SUKISU teams — root support
