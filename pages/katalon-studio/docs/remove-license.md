---
title: "Remove a license"
sidebar: katalon_studio_docs_sidebar
permalink: katalon-studio/docs/remove-license.html
redirect_from:
description:
---

> Requirements:
>
> You must be the Owner or Admin of your Organization to access the **License Management** page. For further details on roles and user management, see: [TestOps User Management](https://docs.katalon.com/katalon-analytics/docs/kt_invite_user_org.html).

On the **License Management** page, you can remove a Licensed User, a machine ID, or a license from a machine ID. To access the **License Management** page, do as follows:

1. Sign in to [Katalon TestOps](https://testops.katalon.io/login).

2. Go to **Settings** > **License Management**.

   The **License Management** page appears.

> Notes:
>
> Contact us at license@katalon.com if you need further help with your licenses.

## Remove a Licensed User

> Notice:
>
> * By clicking **Remove**, you immediately terminate the current session that User is working on with their online licenses in Katalon Studio. You should remove a Licensed User with caution.
> * Removing a Licensed User working with an offline license does not revoke the license.

When you remove a Licensed User, their associated machine IDs are also removed from the Registered Machine list. This action removes assigned licenses from that User and those licenses are available to be attributed again. That User can still use the free Katalon product.

Follow these steps:

1. Go to the **License Management** page.

2. In the **Licensed User** section, click on the *Trash bin* icon of the User for which you want to unassign the license.

   The **Remove** box appears as below.

   <img src="https://github.com/katalon-studio/docs-images/raw/master/katalon-studio/docs/license-mgt/remove-user-popup-2021decUI.png" width=100% alt="remove user popup">

3. Click **Remove** to confirm your action.

## Remove a license

This action removes a license associated with a machine ID. This license is then available to be attributed again. The User that was using the license can still use the free Katalon product.

> Notice:
>
> By clicking **Remove**, you immediately terminate the current session that machine ID is working on in Katalon Studio. You should remove a license from a machine ID with caution.

Follow these steps:

1. Go to the **License Management** page.

2. In the **Online Licenses** section, click on the *Trash bin* icon of the machine ID for which you want to remove the license.

   The **Remove license** box pops up.

3. Click **Remove** to confirm your action.

> Notes:
>
> * You cannot remove an offline license from a machine until the license is expired.
>
> * You can remove Katalon Studio Enterprise's (KSE) **Online Licenses** only. For Katalon Runtime Engine (KRE), see: [Manage Katalon Licenses](https://docs.katalon.com/katalon-studio/docs/license-management.html#transfer-a-license).

## Remove a registered machine ID

This action removes the license associated with a registered machine ID. This license is then available to be attributed again. The User who had their machine ID removed from the registered machine ID list can still use the free Katalon product.

Follow these steps:

1. Go to the **License Management** page.

2. Scroll down to the **Registered Machines** section.

3. Click on the *Trash bin* icon of the machine ID you want to remove.

   The **Deactivate Machine** box pops up.

4. Click **Remove** to confirm your action.

> Notes:
>
> * You can also remove machine IDs associated with a Licensed User by following this guide: [Remove Licensed Users](https://docs.katalon.com/katalon-studio/docs/remove-license.html#remove-a-licensed-user).
