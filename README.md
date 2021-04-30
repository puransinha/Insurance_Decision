# Insurance_Decision

# Health Insurance Decision

Should We Be on the Same Health Care Plan?
When an employer removes a health care plan option, it can leave an individual with fewer choices. But given a domestic relationship, there is another option of deciding to join the second individual's plan. But which is the better option - retaining separate plans, or being on the same plan? Instead of focusing on what was lost (the plan no longer available) it might be more productive to focus on options that are available - choosing a different plan offered by the employer, or having a shared plan.

For some basic background, the plans simulated here are similar in that they both offer a health savings account (HSA), and then have a relatively reasonable monthly premium, along with a maximum out of pocket. As you might guess, when you add a second party to a single person's plan, the out of pocket maximum increases appropriately, the deductible doubles, and the monthly premium also increases.

Some caveats - this breakdown is specific to two similar plans offered by specific individual employers (not stated). As you read this, keep in mind that some expenses are covered at differenet rates (for example, preventative might be covered at 100%), that the calculation doesn't take into account tax benefits from HSA, and that there's other tax implications of being on the same plan as domestic partners that weren't covered here.

The Challenge
We would want to be able to simulate different spending scenarios to determine which option might be better.

Summary of Terms
Before we dive into equations, let's briefly review some of these terms. I am in no way an expert, so please excuse the generalizations.

Health Savings Account
A health savings account is basically a "triple tax advantage" account, which means that we don't pay taxes in three respects:

the contributions that I or my employer might make are not taxed
I'm allowed to invest the money (for example, buy stocks) and when I invest I don't pay taxes.
when I make withdrawals I don't pay taxes
The catch is that you can only use it for healthcare, and there is a maximum contribution that we can make, set by the federal government [ref].

Premium
The premium comes down to how much is taken out of your paycheck each pay period (typically two weeks). This is independent of everything else - if you went through an entire year and didn't have a single medical charge, you'd still be paying for this. And you'd be receiving the HSA contribution in the same way.

Deductible
The deductible (usually between 1 and 2k, and higher for families and couples) is the amount that you must pay out of pocket before insurance kicks in. For example, if I go to some doctor and have a  200𝑐ℎ𝑎𝑟𝑔𝑒,𝑖𝑓𝑚𝑦𝑑𝑒𝑑𝑢𝑐𝑡𝑖𝑏𝑙𝑒𝑖𝑠 1750 I'll have to pay all of that. I can choose to use my HSA or not - in both cases it goes toward the deductible. The deductible is the maximum amount that you have pay (usually over a calendar year) before the insurance starts kicking in. Here is a nice summary of average healthcare deductibles.

Out of Pocket Maximum
Of course if you were to go to the doctor 10 times, each time getting a charge of $200, you would eventually hit a total of $2000. Since this is above the deductible, insurance would have kicked in at the $1751st dollar. The remaining $250 is now subject to the terms of your insurance for whatever is being charged. For example, let's say that I got a procedure that I can look up to see is covered 20%/80% by my insurance. This means that the insurance will (off the bat) cover 80% of the charges, or 80% of $250 ($200). This leaves $50 (the 20%) that I'm responsible for. Now we can discuss out of pocket maximum. In a good year, you'll likely have tiny medical charges for check ups and various prescription medications. But let's say you have a horrific life event, and wind up in the Emergency Room with imaging, staying overnight, and a final bill that is $150,000. Ouch. It might still be the case that you insurance covers a 20/80% split. This means that they will cover 80% (or $120,000) and that leaves you with 20 percent or $30,000. Crap! This is where the out of pocket maximum kicks in. You would only pay up to your out of pocket maximum (depending on the type of insurance, this can vary a lot - I've seen between 3K and 7K) and then insurance is responsible for the rest. So, despite the $150,000 bill, you would only pay (after the deductible and HSA) a maximum equal to your out of pocket maximum. The total expenses would be

premiums - [HSA seed] + [out of pocket max]
The Challenge
Now that we understand the general terms, you probably have a better sense for the challenge at hand. Having a shared plan will mean greater out of pocket maximums, and premiums, but could turn out to be a better deal given that involved parties both have serious medical expenses. You know, all it really takes is one unexpected trip to the ER with a nice ambulance ride to totally screw you (at least if you didn't have insurance!) With this in mind, I wanted to create a basic model for different spending scenarios. Let's start with imports, and functions.
