---
title: Exportation des informations sur les abonnements | Microsoft Docs
author: evanwindom
ms.author: jaunger
manager: evelynp
ms.date: 03/14/2018
ms.topic: Get-Started-Article
description: Découvrez comment exporter une liste d’abonnés et des informations de leurs attributions d’abonnement.
ms.prod: vs-subscription
ms.technology: vs-subscriptions
searchscope: VS Subscription
ms.openlocfilehash: 9b2e03235391826c7a8cc486089a5a3e6384b09a
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39635880"
---
# <a name="exporting-subscription-information"></a>Exportation des informations sur les abonnements

Dans le [portail d’administration](https://manage.visualstudio.com) des abonnements Visual Studio, vous pouvez exporter la liste de vos utilisateurs, ainsi que les informations concernant leurs affectations. Ces informations comprennent : nom, adresse e-mail, adresse e-mail alternative, niveau d’abonnement, date d’attribution, état d’activation, date d’expiration, champ de référence, téléchargements activés, pays, langue, état de l’abonnement et GUID d’abonnement. 

Cette fonctionnalité est utile pour certains scénarios, tels que le suivi des affectations et les dates d’expiration. Par exemple, si vous passez de l’utilisation des BAN aux GUID pour le suivi des affectations d’abonnements, vous pouvez utiliser ce rapport avec la formule VLOOKUP dans Microsoft Excel pour mettre les abonnés en correspondance de façon appropriée.  

Pour effectuer l’exportation, il suffit de sélectionner l’onglet **Exportation** : le fichier est alors téléchargé sur votre machine locale. Le fichier inclut le nom du compte de ce contrat qui contient les abonnements de vos utilisateurs, ainsi que la date de l’exportation.  
> [!div class="mx-imgBorder"]
> ![Exporter des abonnés](_img\exporting-subscriptions\exporting-subscriptions.png)
