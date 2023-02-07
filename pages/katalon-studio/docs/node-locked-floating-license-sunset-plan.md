---
title: "Sunsetting plan for node-locked and floating licenses"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/node-locked-floating-license-sunset-plan.html
description:
---

## Change to licensing model

The licensing model for Katalon Studio Enterprise (KSE) and Katalon Runtime Engine (KRE) is changing.
KSE node-locked and floating license types as well as KRE node-locked license types are being deprecated. The licensing model for both products is transitioning to the following:

* KSE node-locked and floating license → KSE per-User license
* KRE node-locked and floating license → KRE floating license

> Important
>
> For existing subscriptions: License prices will remain unchanged for all existing billing cycles that end before June 7th, 2022.
>
> To learn more about per-user and other license types, refer to <a href="https://docs.katalon.com/katalon-studio/docs/license.html">Types of licenses</a>.

<details>
<summary><strong>Node-locked vs floating license</strong></summary>

<table>
	<tbody>
		<tr>
			<td><strong>Node-locked license</strong></td>
			<td><strong>Floating license</strong></td>
		</tr>
		<tr>
			<td>
				<p>One license is assigned to one machine ID.</p>
			</td>
			<td>One license is assigned to one execution session and can be shared between 3 machines.</td>
		</tr>
		<tr>
			<td>
				<p>Licenses are transferable.</p>
			</td>
			<td>Licenses need to be assigned.</td>
		</tr>
		<tr>
			<td>
				<p>Applies to local desktops or workstations with fixed hardware specifications.</p>
			</td>
			<td>&nbsp;Applies to all types of execution environments.</td>
		</tr>
		<tr>
			<td>
				<p>Online subscription available.</p>
			</td>
			<td>Online subscription available.</td>
		</tr>
		<tr>
			<td>
				<p>Offline licenses can be generated from online node-locked licenses.</p>
			</td>
			<td>Offline licenses are available for on-premises licensing server only. For more information, <a href="https://www.katalon.com/book-a-demo/">contact sales</a>.</td>
		</tr>
	</tbody>
</table>

### Node-Locked License

This license type is applied to local desktops or workstations with fixed hardware specifications (machine-blocked license), such as:

* A virtual machine with a fixed machine ID
* A physical machine

With node-locked licenses, one machine running tests = one license.

* A license is tied to a single machine ID and only for one execution session at a time.
* A machine can be mapped to multiple licenses if needed.
* For machines connected to the internet, the licenses can be transferred to other machines at no cost and as many times as needed.
* For _annual licenses_ only: Licenses can be converted to be used in an offline environment. Once converted, the license cannot be transferred to another machine until it is expired.
* Licenses purchased on a monthly basis cannot be converted for use in an offline environment.

### Floating License

For scaling teams with dynamic usage, floating licenses reduce the management cost and optimize your workflow.

This license type is applied to all types of execution environments, including cloud or virtual machines with dynamic hardware specifications (to execute tests in Docker, Azure, AWS).

* One floating license can be shared across a maximum of 3 machines.
* One floating license is assigned to one execution session at a time.

For instance, you have 1 floating Katalon Studio Enterprise license attached to the email example@katalon.com.

You can use example@katalon.com to log in to Katalon Studio on up to 3 different machines, but not at the same time. This is because  example@katalon.com represents only 1 floating Katalon Studio Enterprise license. Therefore, you can only be active on 1 of those 3 machines at a time.
</details>

## Transition plan for monthly subscriptions

> Notes:
>
> * This section is only applicable to users who have purchased licenses on a monthly, auto-renewed subscription plan, before March 7th, 2022.

Changes will only affect your subscription during the renewal of your license plan, and will have different outcomes depending on the date of renewal. A grace period of 3 months is set during which changes to license prices will not affect the price of your licenses, regardless of your license types. The grace period ends on June 7th, 2022.

* Before June 7th, 2022, you will retain the same license types at the same cost.
* After June 7th, 2022, renewed monthly subscriptions will automatically transition to the new license types, as mapped above, and at the listed price. 
* Additional costs will only affect plans that are renewed after the end of the grace period.

    For example: Suppose you have purchased a node-locked license for KRE that renews on the 14th of each month. From March to April 14th, this will remain a node-locked license. You decide to buy an extra node-locked license at the same price as the previous one. On June 14th, both licenses become floating licenses at the listed price. On June 14th, your billing now reflects the cost of two floating licenses.

> Notes:
>
> * If you have two different billing cycles for KSE node-locked and floating, contact the Success team at success@katalon.com

## Technical support for annual or multi-year contract
If you currently have an annual or multi-year contract, deprecating license types will continue to function as expected until the end of your current contract. Once that contract ends, only new license types will be available for use. 

> Notes:
>
> * For KSE, floating and node-locked licenses cannot co-exist with per-User licenses. You cannot directly purchase per-User licenses until your contract expires or you decide to transition to the new license model. You can contact the Success team at success@katalon.com, if you want to immediately convert to the per-User licensing model.
>
## Migration mapping of KSE floating/node-locked to KSE per-User licenses

### Case 1: Automatic transition to KSE per-User licenses 

This case applies to those of you whose license renewal date is due, and happens automatically.

Consider a scenario where you are a group of 5 users. You have the following licenses at your disposal:

  * 1 generated Offline floating license.
  * 3 floating licenses. 
  
As you can see above, the number of people in your group (5 users) is more than the number of licenses itself (3 floating licenses). Thus, when the license renewal date approaches, 3 KSE per-User licenses are issued to your group, based on the following order of priority:

  * 1 user who has an Offline floating license.
  * 2 unique users who are last seen active.

Thus, you can say:

*N Offline licenses + O unique last active users  = P licenses*

In general, if you have 1,3,4,5……n KSE floating licenses, an equivalent number of last active users receive corresponding per-User licenses.

### Case 2: Manual transition to KSE per-User licenses

This case applies to those who wish to upgrade Katalon licenses or switch to the KSE per-User licenses while the license renewal date is not due.

Consider a scenario where you are a group of 5 users and wish to transition to per-User licenses. To do this:

1. Go to the [Katalon Pricing](https://www.katalon.com/pricing/) page, select **Katalon Studio**, on the KSE per-User plan, click **Buy now**.

	Alternatively, you can sign in to [Katalon TestOps](https://testops.katalon.io/login), then go to **Settings** > **Subscription Management**, select **Katalon Studio**, and click **Subscribe** on the KSE per-User plan.

2. By doing so, you are prompted to confirm whether you wish to merge your existing floating/node-locked licenses to new per-User licenses.

Once you confirm your interest for the transition to per-User licenses, the licenses are assigned to you on order of priority, as it was during automatic renewal.

In case you want to upgrade your plan, after finishing the transition, log into [Katalon TestOps](https://testops.katalon.io/) to upgrade your plan. See: [Upgrade Billing Plan](https://docs.katalon.com/katalon-studio/docs/upgrade-subs.html#purchase-more-licenses).

## Migration mapping of KRE floating/node-locked to KRE floating licenses

Depending on the KRE licenses you currently have, the following cases apply.

### Case 1: Users with monthly KRE node-locked licenses only

You can still use the current KRE node-locked licenses until their renewal date but you cannot upgrade the number of KRE node-locked licenses anymore because KRE node-locked licenses are deprecated from June 7th, 2022. If the renewal date is after June 7th, KRE node-locked licenses will be converted into KRE floating licenses.

If you do not cancel the monthly KRE node-locked licenses, they are automatically renewed and converted into monthly KRE floating licenses after June 7th. You then can upgrade the number of monthly KRE floating licenses.

If you need more KRE licenses before June 7th, you should cancel the monthly subscription of KRE node-locked first, then subscribe to the new KRE floating with a desired number of licenses.

> Notice:
>
> * Make sure you cancel KRE node-locked subscriptions before subscribing to the new KRE floating licenses to avoid additional charges.

### Case 2: Users with KRE node-locked and KRE floating licenses

You can still use the current KRE node-locked licenses until their renewal date but you cannot upgrade the number of KRE node-locked licenses anymore because KRE node-locked licenses are deprecated from June 7th, 2022.

If you do not cancel the KRE node-locked licenses, they are automatically renewed and converted into KRE floating licenses after June 7th.
For example, you have 2 KRE node-locked and 3 KRE floating licenses. If you do not cancel the KRE node-locked subscription, your KRE node-locked licenses will be renewed automatically after June 7th and have become KRE floating licenses. You then have a total of 5 KRE floating licenses from June, 8th.

You can upgrade KRE floating licenses normally. There is no change in the workflow.

### Case 3: Users with KRE floating licenses only

You can upgrade KRE floating licenses normaly. There is no change in the workflow.
