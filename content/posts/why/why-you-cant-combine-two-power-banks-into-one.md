---
title: "Why You Can’t Combine Two Power Banks into One Beast"
date: 2025-05-11T12:40:03+05:30
author: "Rohan Batra"
description: "Exploring the myth of merging two power banks into a single higher-capacity unit by chaining them together. Here's why it fails in practice."
tags: ["power bank", "battery life", "tech myth", "charging", "pTron", "energy efficiency"]
categories: ["Tech Experiments", "Why"]

---

## Can You Make One Power Bank From Two Smaller Units?

> Spoiler: **Plugging one power bank into another and calling it a 40,000mAh beast is just a game of electrical hot potato.** It’s clever in theory—but a terrible idea in reality.

---

## 1. The Temptation

I’ve got **two identical pTron Dynamo Surge 20,000mAh Power Banks** right here. They’re solid, fast-charging, and loaded with protection features. Naturally, the thought struck:

> "What if I just plug one into the other and boom—create a 40,000mAh superbank?"

While I was working on an SOP to **most efficiently charge my DJI Action** during travels (where minimizing the number of devices I have to handle seemed practical), this idea of combining power banks popped into my mind to reduce the hassle of managing them as separate units.

But now, after testing and learning more, I realize **this is not the way to go.**

---

## 2. The Setup

For this experiment, the gear in hand includes:

* **Two pTron Dynamo Surge 20,000mAh** units
* Each supports **22.5W fast output**, PD, VOOC, Dash, Warp
* USB-A & USB-C outputs, USB-C input
* Smart protections for heat, voltage, and current

Here’s the imagined setup:

```

Power Bank A  -->  Power Bank B  -->  Phone/DJI

```

So, the energy path becomes: **Bank A → Bank B → Phone**

Seems like you’re "combining" power. But let’s break down why this doesn’t hold up.

---

## 3. Why This "One from Two" Fails Miserably



### 🔁 Double Conversion Losses

Power banks store energy at \~3.7V internally. To output power via USB, they boost it to 5V+.
When another bank receives that, it *reduces* it back to 3.7V to store it again.

Each of these steps loses about **10–15% energy**. Multiply that across the chain:

#### Real-world Loss Chain:

```

Bank A → ~18,000mAh usable
↓ (boost)
Bank B → ~16,000mAh received
↓ (buck)
Stored in Bank B → ~13,500mAh stored
↓ (output boost)
To Phone → ~11,000mAh to phone

```

You’ve lost **nearly 40%** of usable energy.

---

### 🔥 Heat and Stress

* Every boost/buck conversion creates **heat**.
* Running this loop stresses both banks, especially when repeated.
* Long-term? You risk **degrading the lithium cells** and port quality.

---

### ⏱ Time Waste

Charging one bank from another? You’re looking at **6–8 hours** depending on port ratings and cable quality.

All that, and you still haven’t charged your phone.

---

### ❌ No, It’s Not a Real 40,000mAh Unit

Even with two banks, you're not making a mega-unit. You’re just:

* Converting energy inefficiently
* Losing power with every jump
* Creating more heat than charge

And the kicker?

> **If you charge your phone directly from just one of these banks, you’ll get better performance than this A → B → Phone daisy chain.**

---

## 4. Why the “Fusion” Illusion is a Trap

You aren’t combining battery *cells*. You're routing electricity through two separate systems.

Unlike internal parallel connections inside a **real 40,000mAh power bank**, this method introduces:

```

Power Bank A  --> Conversion  --> Power Bank B  --> Conversion --> Phone 
  
|                           |

Energy Loss              Energy Loss

```

* Redundant circuits
* Conversion overhead
* Thermal stress
* No gain in actual capacity

It’s like pouring water between two buckets and expecting it to double.

---

## 5. What Actually Works Better

💡 Here’s what I do—and what you should too if you’ve got two units:

✅ Use them **independently**—one per device.

✅ **Alternate use**—when one dies, switch to the other.

✅ Travel with both—they're compact and give you double uptime.

✅ Want one big battery? **Buy a genuine 40,000mAh bank** built with proper internal wiring and load balancing.

---

## 6. Final Word

**I tried it so you don’t have to.** Plugging one pTron into another and pretending it’s a massive combined beast doesn’t work—not in physics, not in efficiency, not in real-world performance.

Two power banks are great—just not as one. Use them smartly, not synthetically.

Your gadgets—and your sanity—will thank you.
