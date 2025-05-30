# iOS Hacking Resources

## Basics

Official references:

- [ARMv8 Instruction Set Overview](https://www.element14.com/community/servlet/JiveServlet/previewBody/41836-102-1-229511/ARM.Reference_Manual.pdf) (short, kinda outdated at this point)
- [ARMv8 Architecture Reference Manual](https://developer.arm.com/docs/ddi0487/latest) (long)
- [ARM A-Profile Exploration tools](https://developer.arm.com/products/architecture/cpu-architecture/a-profile/exploration-tools) (same as above, but in machine readable form)
- [ARM System Architecture Software Standards](https://developer.arm.com/architectures/system-architectures/software-standards) (ABIs, extensions, etc.)
- [Clang Pointer Authentication ABI](https://github.com/apple/llvm-project/blob/apple/main/clang/docs/PointerAuthentication.rst)

My own doing:

- [arm64 assembly crash course](https://github.com/Siguza/ios-resources/blob/master/bits/arm64.md)
<!-- TODO: something about memory regions and access permissions -->
<!-- TODO: something about C++ vtables -->
<!-- TODO: something about symbol stubs -->

> [!TIP]
> Both `infocenter.arm.com` and `developer.arm.com` are outright nightmares to navigate, and search engines don't help either. But if you have any ARM document as a PDF and want to check for a newer version, there is a neat trick. At the bottom of any page of the PDF, you should have a document identifier like so:
>
> ![Screenshot](https://user-images.githubusercontent.com/1659374/60986368-9cc60100-a33f-11e9-8ee6-b7dd89f0231e.png)
>
> That should have the form `ARM XXX ddddX.x`. Take the three letters and following four digits, convert them to lower case (in this case, `ddi0406`) and construct an URL like so:  
> `https://developer.arm.com/docs/XXXdddd/latest` (in this case `https://developer.arm.com/docs/ddi0406/latest`)

## Internals

**Mach-O**

- m4b - [Mach-O binaries](http://www.m4b.io/reverse/engineering/mach/binaries/2015/03/29/mach-binaries.html)
- Jonathan Levin - [DYLD DetaYLeD](http://www.newosxbook.com/articles/DYLD.html) <!-- Aug 2013 -->
- Jonathan Levin - [Code Signing](http://www.newosxbook.com/articles/CodeSigning.pdf) <!-- April 2015 -->

**Sandbox**

- Jonathan Levin - The Apple Sandbox ([Video](https://youtu.be/mG715HcDgO8) and [Slides](http://newosxbook.com/files/HITSB.pdf)) <!-- Sep 2016 -->
- iBSparkes - [Breaking Entitlements](https://sparkes.zone/blog/ios/2018/04/06/diving-into-the-kernel-entitlements.html) <!-- Apr 2018 -->
- stek29 - [Shenanigans, Shenanigans!](https://stek29.rocks/2018/12/11/shenanigans.html) <!-- Dec 2018 -->
- argp - [vs com.apple.security.sandbox](https://census-labs.com/media/sandbox-argp-csw2019-public.pdf) <!-- March 2019 -->

**IPC**

- Apple - Mach ([Overview](https://developer.apple.com/library/content/documentation/Darwin/Conceptual/KernelProgramming/Mach/Mach.html) and API documentation (inside the [XNU source](https://github.com/apple-oss-distributions/xnu) in `osfmk/man/index.html`))
- nemo - [Mach and MIG](https://www.exploit-db.com/papers/13176/) (examples are outdated and for PPC/Intel, but descriptions are still accurate) <!-- 2006 -->
- Ian Beer - Apple IPC ([Video](https://vimeo.com/127859750) and [Slides](https://thecyberwire.com/events/docs/IanBeer_JSS_Slides.pdf)) <!-- May 2015 -->

**File Systems**

- Apple - [APFS Reference](https://developer.apple.com/support/apple-file-system/Apple-File-System-Reference.pdf)
- stek29 - [LightweightVolumeManager::\_mapForIO](https://stek29.rocks/2018/01/22/lwvm-mapforio.html) <!-- Jan 2018 -->
- bxl1989 - [Understanding and Attacking Apple File System](https://bxl1989.github.io/2019/01/17/apfs-remount.html) <!-- Jan 2019 -->

**Kernel**

- Apple - [Kernel Programming Guide](https://developer.apple.com/library/content/documentation/Darwin/Conceptual/KernelProgramming)
- Apple - [IOKit Fundamentals](https://developer.apple.com/library/content/documentation/DeviceDrivers/Conceptual/IOKitFundamentals)
- Apple - [About the Virtual Memory System](https://developer.apple.com/library/content/documentation/Performance/Conceptual/ManagingMemory/Articles/AboutMemory.html)
- qwertyoruiopz - Attacking XNU (Part [One](https://web.archive.org/web/20160131061526/http://blog.qwertyoruiop.com/?p=38) and [Two](https://web.archive.org/web/20160131061526/http://blog.qwertyoruiop.com/?p=48)) <!-- July 2015 -->
- Stefan Esser - [Kernel Heap](https://web.archive.org/web/20220819043107/https://gsec.hitb.org/materials/sg2016/D2%20-%20Stefan%20Esser%20-%20iOS%2010%20Kernel%20Heap%20Revisited.pdf) <!-- Aug 2016 -->
- stek29 - [NVRAM lock/unlock](https://stek29.rocks/2018/06/26/nvram.html) <!-- Jun 2018 -->

**Kernel Integrity**

- xerub - [Tick Tock](https://xerub.github.io/ios/kpp/2017/04/13/tick-tock.html)
- Siguza - [KTRR](https://blog.siguza.net/KTRR/)
- Jonathan Levin - [Casa de PPL](http://newosxbook.com/articles/CasaDePPL.html)
- Brandon Azad - KTRW: The journey to build a debuggable iPhone ([Blog Post](https://googleprojectzero.blogspot.com/2019/10/ktrw-journey-to-build-debuggable-iphone.html) and [Video](https://media.ccc.de/v/36c3-10806-ktrw_the_journey_to_build_a_debuggable_iphone))

**Control Flow Integrity**

- Brandon Azad - [Examining Pointer Authentication on the iPhone XS](https://googleprojectzero.blogspot.com/2019/02/examining-pointer-authentication-on.html)
- Qualcomm Product Security - [Pointer Authentication on ARMv8.3](https://www.qualcomm.com/media/documents/files/whitepaper-pointer-authentication-on-armv8-3.pdf)
- Roberto Avanzi - The QARMA Block Cipher Family ([Paper](https://eprint.iacr.org/2016/444.pdf) and [Presentation](https://www.nuee.nagoya-u.ac.jp/labs/tiwata/fse2017/slides/05-02.pdf))
- Roberto Avanzi - [Crypto that is Light to Accept](https://web.archive.org/web/20201216030432/http://tce.webee.eedev.technion.ac.il/wp-content/uploads/sites/8/2016/05/light-crypto-public-2016.04.20.pdf)
- Rui Zong and Xiaoyang Dong - [Meet-in-the-Middle Attack on QARMA Block Cipher](https://eprint.iacr.org/2016/1160.pdf)

**Hardware Mitigations**

- Siguza - [APRR](https://blog.siguza.net/APRR/)
- Siguza - [PAN](https://blog.siguza.net/PAN/)
- Sven Peter - [SPRR & GXF](https://blog.svenpeter.dev/posts/m1_sprr_gxf/)
- VoidiStaff - [JITCage](https://web.archive.org/web/20230210051217/https://voidistaff.github.io/safari/2023/01/01/about-jitcage-on-ios.html)

**Software Mitigations**

- blacktop - [Anatomy of Lockdown Mode](https://github.com/blacktop/presentations/blob/main/0x41con_2023/PDF/AnatomyOfLockdownMode.pdf)
- Csaba Fitzl - [Launch and Environment Constraints Deep Dive](https://theevilbit.github.io/posts/launch_constraints_deep_dive/)

**Web**

- Samuel Groß & Amy Burnett - Attacking JavaScript Engines in 2022 ([Video](https://www.youtube.com/watch?v=FK2-1FAbbXA) and [Slides](https://saelo.github.io/presentations/offensivecon_22_attacking_javascript_engines.pdf))

**Remote Targets**

- Natalie Silvanovich - [The Fully Remote Attack Surface of the iPhone](https://googleprojectzero.blogspot.com/2019/08/the-fully-remote-attack-surface-of.html)

**Hardware**

- Ramtin Amin - [Lightning Connector](https://web.archive.org/web/20220107101537/http://ramtin-amin.fr/tristar.html)
- Ramtin Amin - [NVMe NAND Storage](https://web.archive.org/web/20200217151015/http://ramtin-amin.fr/nvmepcie.html)
- Ramtin Amin - [iPhone PCIe (dumping the 6s BootROM)](https://web.archive.org/web/20200217151824/http://ramtin-amin.fr/nvmedma.html)
- Nyan Satan - [Apple Lightning](https://nyansatan.github.io/lightning/)

**SEP**

- Tarjei Mandt, Mathew Solnik, David Wang - [Demystifying the  Secure Enclave Processor](https://www.blackhat.com/docs/us-16/materials/us-16-Mandt-Demystifying-The-Secure-Enclave-Processor.pdf)
- David Wang, Chris Wade - [SEPOS: A Guided Tour](https://data.hackinn.com/ppt/2018%E8%85%BE%E8%AE%AF%E5%AE%89%E5%85%A8%E5%9B%BD%E9%99%85%E6%8A%80%E6%9C%AF%E5%B3%B0%E4%BC%9A/SEPOS%EF%BC%9AA%20Guided%20Tour.pdf)

**Bootloader**

- Jonathan Levin - [iBoot](http://newosxbook.com/bonus/iBoot.pdf)

**Memory Safety**

- Saar Amar - [An Armful of CHERIs](https://msrc-blog.microsoft.com/2022/01/20/an_armful_of_cheris/)
- Saar Amar - Security Analysis of MTE Through Examples ([Video](https://www.youtube.com/watch?v=LV8BK1ns1Ow) and [Slides](https://github.com/saaramar/security_analysis_mte/blob/main/Security%20Analysis%20of%20MTE%20Through%20Examples.pdf))
- Saar Amar - Firebloom ([Introduction](https://saaramar.github.io/iBoot_firebloom/), [Type descriptors](https://saaramar.github.io/iBoot_firebloom_type_desc/))

## Write-Ups

- geohot - [evasi0n7](http://geohot.com/e7writeup.html)
- Jonathan Levin - TaiG 8.0 - 8.1.2 (Part [One](http://www.newosxbook.com/articles/TaiG.html) and [Two](http://www.newosxbook.com/articles/TaiG2.html))
- Jonathan Levin - TaiG 8.1.3 - 8.4 (Part [One](http://www.newosxbook.com/articles/28DaysLater.html) and [Two](http://www.newosxbook.com/articles/HIDeAndSeek.html))
- Jonathan Levin - [Who needs task_for_pid anyway?](http://newosxbook.com/articles/PST2.html)
- qwertyoruiopz - [About the “tpwn” Local Privilege Escalation](https://web.archive.org/web/20160131055957/http://blog.qwertyoruiop.com/?p=69)
- Ian Beer - [task_t considered harmful](https://googleprojectzero.blogspot.ch/2016/10/taskt-considered-harmful.html)
- jndok - [Exploiting Pegasus on OS X](https://jndok.github.io/2016/10/04/pegasus-writeup/)
- Siguza - [Exploiting Pegasus on iOS](https://blog.siguza.net/cl0ver/)
- Ian Beer - mach_portal ([write-up](https://project-zero.issues.chromium.org/issues/42452496#comment3) and [presentation slides](https://project-zero.issues.chromium.org/action/issues/42452496/attachments/59037116?download=false))
- Ian Beer - [Exception-oriented exploitation on iOS](https://googleprojectzero.blogspot.ch/2017/04/exception-oriented-exploitation-on-ios.html)
- Jonathan Levin - [Phœnix](http://newosxbook.com/files/PhJB.pdf)
- Gal Beniamini - Over The Air (Parts [One](https://googleprojectzero.blogspot.ch/2017/09/over-air-vol-2-pt-1-exploiting-wi-fi.html), [Two](https://googleprojectzero.blogspot.ch/2017/10/over-air-vol-2-pt-2-exploiting-wi-fi.html) and [Three](https://googleprojectzero.blogspot.ch/2017/10/over-air-vol-2-pt-3-exploiting-wi-fi.html))
- Siguza - [v0rtex](https://blog.siguza.net/v0rtex/)
- Ian Beer - [async_wake_ios](https://project-zero.issues.chromium.org/issues/42450458#comment4)
- Siguza - [IOHIDeous](https://blog.siguza.net/IOHIDeous/)
- Jonathan Levin - QiLin ([PDF](http://newosxbook.com/QiLin/qilin.pdf) and [API](http://newosxbook.com/QiLin/))
- Brandon Azad - [A fun XNU infoleak](https://bazad.github.io/2018/03/a-fun-xnu-infoleak/)
- jeffball - [Heap overflow in necp_client_action](https://github.com/grimm-co/NotQuite0DayFriday/blob/bcd6a4f21fb12ac058e67a0b93e5f2a3640fc253/2018.04.06-macos/notes.txt)
- xerub - [De Rebus Antiquis](https://xerub.github.io/ios/iboot/2018/05/10/de-rebus-antiquis.html)
- Ian Beer - [multi_path](https://project-zero.issues.chromium.org/issues/42450613#comment4)
- Brandon Azad - [blanket](https://github.com/bazad/blanket)
- Brandon Azad - [voucher_swap](https://googleprojectzero.blogspot.com/2019/01/voucherswap-exploiting-mig-reference.html)
- iBSparkes - [MachSwap](https://sparkes.zone/blog/ios/2019/04/30/machswap-ios-12-kernel-exploit.html)
- Ian Beer - [Splitting atoms in XNU](https://googleprojectzero.blogspot.com/2019/04/splitting-atoms-in-xnu.html)
- Natalie Silvanovich - [The Many Possibilities of CVE-2019-8646](https://googleprojectzero.blogspot.com/2019/08/the-many-possibilities-of-cve-2019-8646.html)
- Google Project Zero - [A very deep dive into iOS Exploit chains found in the wild](https://googleprojectzero.blogspot.com/2019/08/a-very-deep-dive-into-ios-exploit.html)
  - Ian Beer - Parts [One](https://googleprojectzero.blogspot.com/2019/08/in-wild-ios-exploit-chain-1.html), [Two](https://googleprojectzero.blogspot.com/2019/08/in-wild-ios-exploit-chain-2.html), [Three](https://googleprojectzero.blogspot.com/2019/08/in-wild-ios-exploit-chain-3.html), [Four](https://googleprojectzero.blogspot.com/2019/08/in-wild-ios-exploit-chain-4.html), [Five](https://googleprojectzero.blogspot.com/2019/08/in-wild-ios-exploit-chain-5.html) and [Implant Teardown](https://googleprojectzero.blogspot.com/2019/08/implant-teardown.html)
  - Samuel Groß - [JSC Exploits](https://googleprojectzero.blogspot.com/2019/08/jsc-exploits.html)
- a1exdandy - [Technical analysis of the checkm8 exploit](https://habr.com/en/company/dsec/blog/472762/)
- Ned Williamson - [SockPuppet](https://googleprojectzero.blogspot.com/2019/12/sockpuppet-walkthrough-of-kernel.html)
- littlelailo - Tales of old: untethering iOS 11 ([Video](https://media.ccc.de/v/36c3-11034-tales_of_old_untethering_ios_11) and [Basic Rundown](https://github.com/JakeBlair420/Spice/blob/master/README.md))
- Samuel Groß - Remote iPhone Exploitation (Parts [One](https://googleprojectzero.blogspot.com/2020/01/remote-iphone-exploitation-part-1.html), [Two](https://googleprojectzero.blogspot.com/2020/01/remote-iphone-exploitation-part-2.html) and [Three](https://googleprojectzero.blogspot.com/2020/01/remote-iphone-exploitation-part-3.html))
- Siguza - [cuck00](https://blog.siguza.net/cuck00/)
- Justin Sherman - [used_sock](https://jsherman212.github.io/2020/02/06/used_sock.html)
- Samuel Groß - [Fuzzing ImageIO](https://googleprojectzero.blogspot.com/2020/04/fuzzing-imageio.html)
- Siguza - [Psychic Paper](https://blog.siguza.net/psychicpaper/)
- Brandon Azad - [One Byte to rule them all](https://googleprojectzero.blogspot.com/2020/07/one-byte-to-rule-them-all.html)
- Brandon Azad - [The core of Apple is PPL: Breaking the XNU kernel's kernel](https://googleprojectzero.blogspot.com/2020/07/the-core-of-apple-is-ppl-breaking-xnu.html)
- windknown - [Attack Secure Boot of SEP](https://github.com/windknown/presentations/blob/master/Attack_Secure_Boot_of_SEP.pdf)
- Ian Beer - [An iOS zero-click radio proximity exploit odyssey](https://googleprojectzero.blogspot.com/2020/12/an-ios-zero-click-radio-proximity.html)
- Alex Plaskett - [Apple macOS 6LowPAN Vulnerability](https://alexplaskett.github.io/CVE-2020-9967/)
- Luca Moro - [Analysis and exploitation of the iOS kernel vulnerability CVE-2021-1782](https://www.synacktiv.com/publications/analysis-and-exploitation-of-the-ios-kernel-vulnerability-cve-2021-1782)
- Alex Plaskett - [XNU Kernel Memory Disclosure](https://alexplaskett.github.io/CVE-2021-30660/)
- Jack Dates - [Exploitation of a JavaScriptCore WebAssembly Vulnerability](https://blog.ret2.io/2021/06/02/pwn2own-2021-jsc-exploit/)
- Mickey Jin - [CVMServer Vulnerability in macOS and iOS](https://www.trendmicro.com/en_us/research/21/f/CVE-2021-30724_CVMServer_Vulnerability_in_macOS_and_iOS.html)
- K³ - [Writing an iOS Kernel Exploit from Scratch](https://secfault-security.com/blog/chain3.html)
- CodeColorist - [Mistuned Part 1: Client-side XSS to Calculator and More](https://blog.chichou.me/2021/08/04/mistuned-part-i/)
- CodeColorist - [Mistuned Part 2: Butterfly Effect](https://blog.chichou.me/2021/08/05/mistuned-part-ii/)
- Justin Sherman - [CVE-2021-30656 kernel info leak](https://jsherman212.github.io/2021/08/19/CVE-2021-30656.html)
- Samuel Groß - [Attacking JavaScript Engines](http://www.phrack.org/issues/70/3.html#article)
- Samuel Groß - [Compile Your Own Type Confusions](http://www.phrack.org/issues/70/9.html#article)
- Adam Donenfeld - [(De)coding an iOS Kernel Vulnerability](http://www.phrack.org/issues/70/8.html#article)
- xerub - [The Bear in the Arena](http://www.phrack.org/issues/70/12.html#article)
- Linus Henze - [Fugu14](https://raw.githubusercontent.com/LinusHenze/Fugu14/master/Writeup.pdf)
- Justin Sherman - [Popping iOS <=14.7 with IOMFB](https://jsherman212.github.io/2021/11/28/popping_ios14_with_iomfb.html)
- Ian Beer & Samuel Groß - [A deep dive into an NSO zero-click iMessage exploit](https://googleprojectzero.blogspot.com/2021/12/a-deep-dive-into-nso-zero-click.html)
- Ian Beer & Samuel Groß - [FORCEDENTRY: Sandbox Escape](https://googleprojectzero.blogspot.com/2022/03/forcedentry-sandbox-escape.html)
- Ian Beer - [CVE-2021-30737, @xerub's 2021 iOS ASN.1 Vulnerability](https://googleprojectzero.blogspot.com/2022/04/cve-2021-30737-xerubs-2021-ios-asn1.html)
- Ian Beer - [CVE-2021-1782, an iOS in-the-wild vulnerability in vouchers](https://googleprojectzero.blogspot.com/2022/04/cve-2021-1782-ios-in-wild-vulnerability.html)
- Ivan Fratric - [DER Entitlements: The (Brief) Return of the Psychic Paper](https://googleprojectzero.blogspot.com/2023/01/der-entitlements-brief-return-of.html)
- Félix Poulin-Bélanger - [kfd](https://github.com/felix-pb/kfd#where-to-find-detailed-write-ups-for-the-exploits)
- Asahi Lina - [AGX Exploit](https://asahilina.net/agx-exploit/)
- Gergely Kalman - [librarian - a macOS TCC bypass in Music and TV](https://gergelykalman.com/CVE-2023-38571-a-macOS-TCC-bypass-in-Music-and-TV.html)
- Ian Beer - [An analysis of an in-the-wild iOS Safari WebContent to GPU Process exploit](https://googleprojectzero.blogspot.com/2023/10/an-analysis-of-an-in-the-wild-ios-safari-sandbox-escape.html)
- DFSEC - [That's FAR-out, Man](https://blog.dfsec.com/ios/2023/11/19/thats-far-out-man/)
- Mickey Jin - [xpcroleaccountd Root Privilege Escalation](https://jhftss.github.io/CVE-2023-42942-xpcroleaccountd-Root-Privilege-Escalation/)
- Alfie CG - [Trigon: developing a deterministic kernel exploit for iOS](https://alfiecg.uk/2025/03/01/Trigon.html)
- Alfie CG & opa334 - [The state of iOS jailbreaking in 2025](https://raw.githubusercontent.com/alfiecg24/Presentations/main/The%20State%20of%20iOS%20Jailbreaking%20in%202025.pdf)
- Siguza - [tachy0n](https://blog.siguza.net/tachy0n/)

## Other Lists

- qwertyoruiopz - iOS Reverse Engineering ([Wiki](https://github.com/kpwn/iOSRE/tree/master/wiki) and [Papers](https://github.com/kpwn/iOSRE/tree/master/resources/papers))
- Google Project Zero - [All the bugs Ian Beer has killed](https://project-zero.issues.chromium.org/issues?q=reporter:(ianbeer@google.com)&s=created_time:desc)
- Google Project Zero - [All Apple bugs](https://project-zero.issues.chromium.org/issues?q=customfield1352808:Apple&s=created_time:desc)
- Google Project Zero - [A survey of recent iOS kernel exploits](https://googleprojectzero.blogspot.com/2020/06/a-survey-of-recent-ios-kernel-exploits.html)

## Community

"Hack Different" is a Discord server about hacking, reverse engineering and development loosely on and around Apple platforms.  
It has a relaxed atmosphere and is a great place to hang out and connect with fellow researchers and enthusiasts.

[![Hack Different](https://discordapp.com/api/guilds/779134930265309195/widget.png?style=banner2)](https://discord.gg/NAxRYvysuc)
