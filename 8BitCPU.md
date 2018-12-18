---
layout: default
comments: true
---

[Back](index)

# 8 Bit CPU from Scratch

I'm currently building a 8-bit CPU based on the tutorial videos done by Ben Eater.

I'm following his series and building each component in order. i thought i would just show off the progress i've made as well as some of my experiences along the way.

I bought my components from Jameco primarily. while other options were availible, i went with the list providied to me to ensure all the components were correct.

Ill break this down into the modules i build them in. My descriptions will be more simplicty for the purposes of demonstration, The video series goes into much great detail on most of the topics I mention.

![an array of logic IC's](https://lh3.googleusercontent.com/XXhVl63iiTH3ZPr1MR-NCaQ79OP9MtKYBLRqM-pFMIXSNIJLwwNvyePGN2yKEmVqS-e2iXeZDIR1mY5cFj0_JFSYX8qxwNoBGNVjQIAjePa8gQRaMu-dLNS-IqDmozezgRCc_BypJSAvNP6ahctSfQ1-l5tCNvFFuYOB5MmcegAsmNlOkdv1EHbBKOx1sVh589sKGRR9GJdlpDpJuyYTD-9A1dJzpdEw8wBtmfLWN-hP8yXqdNREoN5_ciLp9eTq2OG1TWQlbNx64VnBsqT4k4Q0yZwNho7CC1RlexLQ8kkZ5zAZqqQLUYMPLt-Gc5LUOp2j32UkLlZyad_j4pgTEydCI43DUJ0FGuVOY0BwleKdKrWaXDk_d1uNsBp_HStjs_qjTup2PSG3WD2qbCiLkOYVJsV4AirEsZSh0FZtGQb4O0jTJ-nuQPmM88ueSZ01I3Z53jZ5FRQAqHTEX2JegNVqUGu9MPEN3ad9JlAH2ZqRl2f4uwqe8H8TrYwXSMOqNj-c_0OPxkPS6e8WBWLkHzU81qV-YO3IrCUgBsTfkI2m42HchVeRJw6oi5hvzO8_KNuFcyBQipCjGwRWGba52jMnmY1XxN5w_sKy6WV5EhEDxH3YFrtzsbQbcWePiAOeAUeu_JItoyW3anYE1bAwkVPmXIs9sFnMkahOMe5KKkjd8aXxN_Hu1-QelVvRoNqZVLAjkp84vxLgMwqmCA=w3840-h1920-no)

> here are some of the chips i was working with.

# Clock

This clock module is designed to act as the heartbeat of the computer, this clock module will also be adjustable through a potentiometer so that we can cahgne the speed of the cpu during its operations. It also features a toggl button to switch between an astable mode and a manuel mode. when in the later, a separate button can be pressed to manueally advance the clock.

here's are the shots of my clock module before and after i cut wires to length. 

![Clock before cut wires](https://lh3.googleusercontent.com/EjKoXvgYaWv4nIPEoFeBqrUXD41T5qFCul-5eFOiRn4KOvhmfbiHsn4irr6V1kwlgsqHKffA-SSaAnQKYrIONW6aqgfWP2F8BkOG6MDmTr6s_1JQ4VJDqLwncHgDogl1XLZ1A-TLJ6-haWNJvhrQh4jVSTQ6u3uNmO9d7rX89rwjIoy4MayIF6zED3aIkFBVvnqsML2KY5Dcphfpp6Xq5AEeqjhmdoLZGEHzF8giyEKyTBg-pUGLJevyfRzHZZDk2n_bN7UmN1ITpfH2x_H3ljhRkGyGxv1QwzROwMs69U9cQUmUy1Ge8Gb-i28MlYZso7sgqLu1aojAhc8FonCO7E9X5KkoR3l2rxugddK8doulrZ1Y0yeHRti86P90teJ2m1hnFxOjPy5BCTaXguKBje89USDeB4IlMcoDi6da5reW-p1hN5BZ6uqi0jtCz79Fzwabu67I3FW5FcCqXG6Ny-4vMm4Ar7HlIPb5OG5aTeJ19VVvBgL4KaLQ_cCHkIGgFJe2gZ0Om_Im3l4fhurGyHwR-Mr5-oDbUFcag9QxHO1mpqtH1p8RWGIedPRel7RPhpRcYST5QFK9dUTWRh1vrM-LePfZkHOkBufKqEsG7EHFQk4pK6a0Zou8uQrxD3Av8RiCQIhv5E2WidjXfCmIBtgNYVDe-5GBdR6LQMCJyWSVCqsFHfL6NfhNBBuqdlKjS3fZ_E7szbyZbbDrGQ=w1213-h910-no)

> wired up using jumper wire. Messy but quick to get going

![Clock after cut wires](https://lh3.googleusercontent.com/0gNa6PT9t8naAwRb4qrnzCAWeKLaHFahvI3wh2MgBrqn3JouR78nNLszKKkhBYLGA2dhFT7o53UDmwlSjatfihZks96bzNHHnBFJvb-SIzaBs7oDb9hOpNGRMhdO4Qi308y_V6ibkGcPa-5BmuH9Vi_60DA3u-x4ErZzGR1iAvKmuXR6vXPVsR_BvL3UaXfxhTSKX4hKXWV_hEH17htmaytrt1u8CBm7J1BcIIv-VYYSPysyiA5K6IeB8gH36Eo0j7FcOS46AXXsGd4B1hajgM5YpSgCJfnDf5LVkQIvGjFdJAMnPkqykg1d3g0tFl_rtcS2GZ2dzbvhsA5VVd9QsT3BIb1zWGFlPOTutwks238_Jc--JSNxy0h_SE2w4G-HcOPucdd35gskYu4kXQ9lk-whVrSpaso8qT3myKc3lGKH4M9HCCTL8pb6FFylv0kWDZRjCZNMb5nvTzLHhAsIzeeWr4tDjiT7kkNKODdrvcz5so0IF71tyXFZ-CA_d8XA6-5DiWgTxSGCuBOwDvbzLclEbk17y6nRMSQ4HQ2RZlE_2vM0MJxwdcFQSh1vbphEWVZjRA99Rqfc1eUlLxF01Zu2ZAckZ4YwGYaoKKCbpxvHc73WwjU0DQKmk-u5aUl7f9i8ostuvYozIFlQEfhbInLo3ZBekzR_fGD0hO04WXINxAdbjac22y7aNgrPwzpSIa5XcFn764KqCf3SVA=w1213-h910-no)

> Clean... but cutting the wires can take quite awhile one of the things that never crossed my mind when starting this project. the magic of video editing made this process seem easy.

## Registers

the next part was to build a register. The purpose of which is to hold, in this case, an 8 bit binary value. like 10010110 for example. functions it should perform are 

- **In** (latch value into the register)
- **Out** (put value out on the bus)

Becuase this is a learning project, there are LED's hooked up to all the output 

![Clock with Register A](https://lh3.googleusercontent.com/p3AgRHZYYjliKMAyylcJw6KWQPD8sBA5weK3WGKusQYQ8hlWf3Oot81E-kQNIJTcGCSKZEUa_J3BAr8F5XiH-U4U-cgG0SF6Gkn2WPwUFN8a0m9w36lTtr-_b-8NG7sp1GHpAAcV8RC1KYpd-NTZZmD00xW2m6tAJGfi5JaHTsh9bGPJT7dT4zsawdVwS5QvkqUcYQDNX7sjtta0TVdCsRR3nsfLrGQkY4wcY-_K9zECsN2kbzMkPuuHfo3UpA923-5co1iTJa5T0_pX_9YNWfE5jEV9Rvxk-ubvZveUxXhpGtmKAYnv9jnAvmtV7sdv2YFYUNEYOGpacP7Zc94Tb7FWito1Nz3WMAvwMVD0-Oq5x3rJL8OU1TOaMKOV_jLgCief9ZTN0KxTIrVvtIn10HEQO7IAme9VbXHLFCqFrNVeaUOdT55JMwPnO3UkAan5tro2Sh8yCiLRne6oOD2RfTjCifM1wq0nofmCL5xwI49hppjB9PnvHYAMscbpUlZhwwn9ZVunZdgbtgOH3Ne2T4KaXcdDwwVDjbu1pnFRLqCnJbjJqq1Xs3eeP9luhpsZ4LyS2JuMSU-9Cg2dOLutxUpHneWah67uzUEKKfySP0fQbEeh7w3QiAm0eSj-YInLA5SjGc5rMdu2y8vs9GYBkX9eSG0KIop-H-r0JsT4tIsWNJihv-lxRKPJ8AqI2itSJGNTC8X7HYhdfs2_7A=w3036-h2276-no)

> Register A (bottom right breadboard) is shown with the value 00000100 stored in it

another register was then build beside this one so that we have 2 saved value to either add or subtract.

## Adder / Subtractor (Simple ALU)

This module allows the CPU to add or subtract the values stored in the aforementioned registers. Here we see a simplistic binary addition of...

00010000 + 00010000 = 00100000

and you can see the coresponding LED's lighting up on the board.

![Clock, Register A & B, ALU](https://lh3.googleusercontent.com/ripwOUh7UEvEuaxdGogsf2ULr2ywvPBm3oddXqD-ZXn5wLaPMI49BWMKSSMDaAcK0FKv4z5hb23IvSJArZd8-n4UNeKB6NeV6OyGYP8ybCpi2KGqs7yic3WWn7sYsaJoEIke3yuX9vbONIY0OPVI5kXhmrJlLY0eQiVNCjcQGlrRzSwe-uND6LT-OV9KXd7ER77THXmzMljo71uJ7TQ4AJ3xg8aAAdTS85wYOOrev3QC1uAQiI3ZWkwyoFUMO-acgeDrWhIgY40JtXrOFSglZzjBXOoZSvPnUZ3ujJDCyyFdzjH8xw4AlHydxFLAjz8ZwGKnF5iEd4Mtyj4BuQEEp2fw56MZNrz0Xx4Dv-QtSbJig39UbxiaFkRQjD7cveOLRWVa8T248r3LwDmKKzDhHh5nLLXdpwICzfgPNXA7483dMPgyRu3SnKc2rc0uAFtiuAI4ve695x7_e13Cl0Aa5tf37eTawGL6w52y0SEHlaZMI9pDGynj5O817D4ckmSlyMF5SNX0KpRTJsd_KDC9UAOdt6ZHmPhXHl1efOmCJpjX7YqJp9_hgFcnqWYIgpK-TA_Ev8Lzr8jo2L-ZgHoJv4ZxutwRQyeuPh5C9vCWNKLRMIm0wLSXV4vf0pDXHTlemgfYzxkBqNc-lMMDEgXOBEkLF0I3Sg6CB-G94YqJTBq3yZoxfDqbVKIOuZ0exIrkLdUq2gz6d_F3A_EWxg=w1213-h910-no)


<link  href="https://cdnjs.cloudflare.com/ajax/libs/viewerjs/1.3.1/viewer.min.css" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/viewerjs/1.3.1/viewer.min.js"></script>

<div>
<div>
<img id="image" src="https://lh3.googleusercontent.com/7I9Riz_XdZ2irjiVkY0zfQaS5nMXGtdodYxFLLoICTfBjGF_nBs70YPNsmtzrQyBSBGEVfISGpk1-75uU4ElpR2yJaNMKKkNSGgegu4WPf4aCfH-T1ZuBV0jO3jmZW_XjQNaq1VvbDVFl_yC_pHj_6prbgMqoQGjXmDNA9Veb851IrhrN-xmrMS0YmiVPaXu4IEA0EIf5xHaB4pavNdM_QzTzg_8ji0NSKqy0blbOsmTTQgnkoVoZP2A1vQZtr-dcZ9qi-xg8QYzRV1UAGD00ds9ZqjsaPIMCTfCik4lvduWmaqEIKAgXAlhHv4ec72wmWxF_58iwTJ1OH9F6ksKA7GGNJKxDwJIZmlIQ8HpAVbGpa_YvULz6Rl_cwY-PEcIGk5-O7epqqKlAGNc2iZN9_1wGep_8v20r3aZcf80FateStDKRMmEGhOn83pTaHevwZxfzLnCC5mKhlOPnH9YE6MZagdZF-xvZxEkqWh99Dt5vBFuO7-nGnHh-25FQwOsAWFCgCOrwYrY2QzbMHyQi3SMlcPFDI9yovjQXbemZQfxWbmNf5GCl-N7qod06xQNN4F9A9uPuK8mNqSCLZG_VziX97AlXJQ-uP_e1xoxzvsNOQJgGfuYrMvhPxNkMvWVGzVoeuJJG6CvC2dYUySGgGt5o0hdcX68oL0HKXYDlpigXUgN6tLhEm8FWQMSpV8JaTxr3oyIxu_AKM9quQ=w1213-h910-no" alt="Picture">
</div>

<div>
<ul id="images">
    <li><img style="max-height:200px;max-width:200px;height:auto;width:auto" src="https://lh3.googleusercontent.com/7I9Riz_XdZ2irjiVkY0zfQaS5nMXGtdodYxFLLoICTfBjGF_nBs70YPNsmtzrQyBSBGEVfISGpk1-75uU4ElpR2yJaNMKKkNSGgegu4WPf4aCfH-T1ZuBV0jO3jmZW_XjQNaq1VvbDVFl_yC_pHj_6prbgMqoQGjXmDNA9Veb851IrhrN-xmrMS0YmiVPaXu4IEA0EIf5xHaB4pavNdM_QzTzg_8ji0NSKqy0blbOsmTTQgnkoVoZP2A1vQZtr-dcZ9qi-xg8QYzRV1UAGD00ds9ZqjsaPIMCTfCik4lvduWmaqEIKAgXAlhHv4ec72wmWxF_58iwTJ1OH9F6ksKA7GGNJKxDwJIZmlIQ8HpAVbGpa_YvULz6Rl_cwY-PEcIGk5-O7epqqKlAGNc2iZN9_1wGep_8v20r3aZcf80FateStDKRMmEGhOn83pTaHevwZxfzLnCC5mKhlOPnH9YE6MZagdZF-xvZxEkqWh99Dt5vBFuO7-nGnHh-25FQwOsAWFCgCOrwYrY2QzbMHyQi3SMlcPFDI9yovjQXbemZQfxWbmNf5GCl-N7qod06xQNN4F9A9uPuK8mNqSCLZG_VziX97AlXJQ-uP_e1xoxzvsNOQJgGfuYrMvhPxNkMvWVGzVoeuJJG6CvC2dYUySGgGt5o0hdcX68oL0HKXYDlpigXUgN6tLhEm8FWQMSpV8JaTxr3oyIxu_AKM9quQ=w1213-h910-no" alt="Picture 1"></li>
    <li><img style="max-height:200px;max-width:200px;height:auto;width:auto" src="https://lh3.googleusercontent.com/Rw320Rs3HaDb9ZzhdT4gqTWQj9LMK6VO1w5SNDYe_mT-QMPi1ZSAnIIzq6R-q_QEuh7RD7mC9n-59RK3NaqioLNc6Mc455NATzsFDUDRn1irNS08PaOyMcnyAC3PY9Ot_kLTf-UhW8Lt1NQD_7aPcfzXmh2yODz99Kp0wC_31-U_QnbumPAoYsMOWwYkbuJ2OCNgqaxot5YoqmON98HF13OZE7c8N3oHw3Alrx9VWGIGSSEa0wKt6-mBfBhsmYrnc6lpMgj2drDNrTkT0RVuvxFAIFmMcrZAHhFfYxmMPFMe3GOM27AxN6GC7lSejpg3vGbGpuXwm97COXQpr761llTbRjBScWhgX-G2NkqmiIWlyQAnbg3jaMb59l8KcobmKZhfRF8Dkqx_A-UJYn_tu1SdXu6wKCpb0ECAIbmd1C_5itEpkluEvdxa3I4ULqnm5TZuIxlKWkaB7rgdz_9Y3Nfl-9qguaMntU7XIqiZCcZQ1feH4DcgQvkEaXfhWl6ZXMPHXaLhUrGec0DYCIwJRQx8G9ZQZ0_vNPDWo290wsyuEdTYcXBkn6alKUp8B38VTqA7EtCXwowXdQ4YGhsqTwYmZEvhQhvV8byqcNPaEoyUn58R0LPYli0coPw6vm8f9kcecFCe6APVeBFSjAZYZF-ZSviXDy1KFgCc4fbZ6ApZNXLkLngWyi9LxQ0OfYGlY34gsefC-3BDguWgrg=w1213-h910-no" alt="Picture 2"></li>
    <li><img style="max-height:200px;max-width:200px;height:auto;width:auto" src="https://lh3.googleusercontent.com/Ib4T9L-fbzz4dDnAOP91IV-h9Z9Pk4fNYq_N5jndsbAob3MFItlb8-43WCcjan9uxNH3XZzsIE8ycX5nr4aEvqgl14ofyYQ7VFwhPuasaIbI85fQL_AU-I0lrn4QycuJ-zJyrzHAo01Oj96-vAOfOpM6TXmU8kKUcIihx2y9g0FrwZxkGdHkeHJGbH7iCQok_H2sjRGcvAW-_WoDv2zEaN236rsBIQnD1XfOevU3N6gTOvu8fz3-ImQbi9UVMw3gphEyu8LB8qth97i6tS-S0KHJcIGY5FDOUivz4vH55X6CpJ_RbvyXz2HNxt6VdIICR4Pu-mwrYzFgdNGWfJKl6H9Y5uhE2UfJ8JvkaSYgTfXuNdC29ViW0G3zSIcFx2Z_4Fclahc03aGs_-d3x7uU7t7qH_S5TMNIfFGXsiNmthDTUVtxJCpi7cbUagmiqvHiuMlOdXRUaVhE7jAddoiEwFvgxfR6nbpx58B1EDrzYaX36vdidZUYe5-8LMe_Oj1Y_G1Gadro5GQ9NZTlNya_dEAWll7uTLlX9VmKvCMJtDKYNr4EYI22P_KWlUBRfHu5M1AlwSdD8YadHROf6zvh_aQLOsN5uA6dzOTiCEFc2_PNDNiWUZzYhyChwkJoriLVIgCHGo3M8k1SvPTomOxXTa9XrXxQ2gGF12mTpCJNejGZu-DKkE5m19R01jFT8hREYYGdeVWNrgZeQjiCuw=w1213-h910-no" alt="Picture 3"></li>
    <li><img style="max-height:200px;max-width:200px;height:auto;width:auto"  src="https://lh3.googleusercontent.com/0cHty5aQY1RxLHNExcYI9d7Yr57zagR91WE40pNburPPEvh4cnI46dWo8zmp9OvcgRnqEHS9ko6hye0Yo7A4ZZGMXyCpCDMrgL1cOIgHwA6B0l0ESxBPrSWDSyAy4OEtJ-sNGP8xDLe-qvJWJjtLAubPSipP3NH_ZCCTNahOFIhihvgVSTa8sgSeMfDoOYeLkgLXIVC2ClBTlM_ASg5LwTORJY3uPQIy1YUFMLOP8Bl4nuFxvdPkg7NocAfpAzTlK4vuyy4BQ45UCf4F7UViMCrrOyLGvSrkQzV3JQ7AB5kNfqDI_4aME4rVYX3l8dAEH7Qr_GGIziBQKxtexrW1sziIp-i7FjQ7x2NAHJkp55rBcXIWusxT3SH-dE8BnEcq8ORAnqpHYa0fittNWE07bKKm84XAadq_f3FApKX0LAILQMTdUmB3nz4gg7mwL5phs09056TajbVeeSSojAl1_huv4zuN_juvoBT0Ct0hv0LghV2WymtVZpXv-BLJHIF0PvmTLVHf3p-fLPuXBtNPGrHfhljXWWWajrzIzUPBe1k3_lJ2uJ6a6vtw5fSsi22BLwRtgt5oNF-7rNio-YOLwl_oEI-OYYgjvfUm7x92i0Uhygo6B-8YVPyymxGSqIrtuRYv4SqxyXttkv78KT2_nsPV0yagAwQWJL8Ka6Qhd5qLH1zbaeGyPXwHVYWvTM2skem_CKYmGHu7ybIVfw=w3036-h2276-no" alt="Picture 3"></li>
</ul>
</div>
</div>

<script>
// View an image
const viewer = new Viewer(document.getElementById('image'), {
  inline: false,
  viewed() {
    viewer.zoomTo(1);
  },
});

// View a list of images
const gallery = new Viewer(document.getElementById('images'));

</script>

## Plans for the future

programmer
compiller
PCB
FPGA

