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
<img id="image" src="picture.jpg" alt="Picture">
</div>

<div>
<ul id="images">
    <li><img src="https://lh3.googleusercontent.com/ripwOUh7UEvEuaxdGogsf2ULr2ywvPBm3oddXqD-ZXn5wLaPMI49BWMKSSMDaAcK0FKv4z5hb23IvSJArZd8-n4UNeKB6NeV6OyGYP8ybCpi2KGqs7yic3WWn7sYsaJoEIke3yuX9vbONIY0OPVI5kXhmrJlLY0eQiVNCjcQGlrRzSwe-uND6LT-OV9KXd7ER77THXmzMljo71uJ7TQ4AJ3xg8aAAdTS85wYOOrev3QC1uAQiI3ZWkwyoFUMO-acgeDrWhIgY40JtXrOFSglZzjBXOoZSvPnUZ3ujJDCyyFdzjH8xw4AlHydxFLAjz8ZwGKnF5iEd4Mtyj4BuQEEp2fw56MZNrz0Xx4Dv-QtSbJig39UbxiaFkRQjD7cveOLRWVa8T248r3LwDmKKzDhHh5nLLXdpwICzfgPNXA7483dMPgyRu3SnKc2rc0uAFtiuAI4ve695x7_e13Cl0Aa5tf37eTawGL6w52y0SEHlaZMI9pDGynj5O817D4ckmSlyMF5SNX0KpRTJsd_KDC9UAOdt6ZHmPhXHl1efOmCJpjX7YqJp9_hgFcnqWYIgpK-TA_Ev8Lzr8jo2L-ZgHoJv4ZxutwRQyeuPh5C9vCWNKLRMIm0wLSXV4vf0pDXHTlemgfYzxkBqNc-lMMDEgXOBEkLF0I3Sg6CB-G94YqJTBq3yZoxfDqbVKIOuZ0exIrkLdUq2gz6d_F3A_EWxg=w1213-h910-no" alt="Picture 1"></li>
    <li><img src="https://lh3.googleusercontent.com/ripwOUh7UEvEuaxdGogsf2ULr2ywvPBm3oddXqD-ZXn5wLaPMI49BWMKSSMDaAcK0FKv4z5hb23IvSJArZd8-n4UNeKB6NeV6OyGYP8ybCpi2KGqs7yic3WWn7sYsaJoEIke3yuX9vbONIY0OPVI5kXhmrJlLY0eQiVNCjcQGlrRzSwe-uND6LT-OV9KXd7ER77THXmzMljo71uJ7TQ4AJ3xg8aAAdTS85wYOOrev3QC1uAQiI3ZWkwyoFUMO-acgeDrWhIgY40JtXrOFSglZzjBXOoZSvPnUZ3ujJDCyyFdzjH8xw4AlHydxFLAjz8ZwGKnF5iEd4Mtyj4BuQEEp2fw56MZNrz0Xx4Dv-QtSbJig39UbxiaFkRQjD7cveOLRWVa8T248r3LwDmKKzDhHh5nLLXdpwICzfgPNXA7483dMPgyRu3SnKc2rc0uAFtiuAI4ve695x7_e13Cl0Aa5tf37eTawGL6w52y0SEHlaZMI9pDGynj5O817D4ckmSlyMF5SNX0KpRTJsd_KDC9UAOdt6ZHmPhXHl1efOmCJpjX7YqJp9_hgFcnqWYIgpK-TA_Ev8Lzr8jo2L-ZgHoJv4ZxutwRQyeuPh5C9vCWNKLRMIm0wLSXV4vf0pDXHTlemgfYzxkBqNc-lMMDEgXOBEkLF0I3Sg6CB-G94YqJTBq3yZoxfDqbVKIOuZ0exIrkLdUq2gz6d_F3A_EWxg=w1213-h910-no" alt="Picture 2"></li>
    <li><img src="https://lh3.googleusercontent.com/ripwOUh7UEvEuaxdGogsf2ULr2ywvPBm3oddXqD-ZXn5wLaPMI49BWMKSSMDaAcK0FKv4z5hb23IvSJArZd8-n4UNeKB6NeV6OyGYP8ybCpi2KGqs7yic3WWn7sYsaJoEIke3yuX9vbONIY0OPVI5kXhmrJlLY0eQiVNCjcQGlrRzSwe-uND6LT-OV9KXd7ER77THXmzMljo71uJ7TQ4AJ3xg8aAAdTS85wYOOrev3QC1uAQiI3ZWkwyoFUMO-acgeDrWhIgY40JtXrOFSglZzjBXOoZSvPnUZ3ujJDCyyFdzjH8xw4AlHydxFLAjz8ZwGKnF5iEd4Mtyj4BuQEEp2fw56MZNrz0Xx4Dv-QtSbJig39UbxiaFkRQjD7cveOLRWVa8T248r3LwDmKKzDhHh5nLLXdpwICzfgPNXA7483dMPgyRu3SnKc2rc0uAFtiuAI4ve695x7_e13Cl0Aa5tf37eTawGL6w52y0SEHlaZMI9pDGynj5O817D4ckmSlyMF5SNX0KpRTJsd_KDC9UAOdt6ZHmPhXHl1efOmCJpjX7YqJp9_hgFcnqWYIgpK-TA_Ev8Lzr8jo2L-ZgHoJv4ZxutwRQyeuPh5C9vCWNKLRMIm0wLSXV4vf0pDXHTlemgfYzxkBqNc-lMMDEgXOBEkLF0I3Sg6CB-G94YqJTBq3yZoxfDqbVKIOuZ0exIrkLdUq2gz6d_F3A_EWxg=w1213-h910-no" alt="Picture 3"></li>
</ul>
</div>
</div>

<script>
// View an image
const viewer = new Viewer(document.getElementById('image'), {
  inline: true,
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

