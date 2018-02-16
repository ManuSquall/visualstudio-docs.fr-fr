---
title: "Abonnements Visual Studio - Renvoi d’e-mails d’attribution à partir de VLSC"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 1/23/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend subscription assignment emails from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 338ae08ee1f3e6a819a1faea7bd095c9acd8ecd2
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-within-volume-license-service-center-vlsc"></a>Guide pratique pour le renvoi d’e-mails d’attribution d’abonnements à partir du Centre de gestion des licences en volume (VLSC)

Il peut arriver qu’un abonné auquel un abonnement a été attribué demande à un administrateur de lui renvoyer l’e-mail de notification d’attribution de l’abonnement.  Dans le nouveau portail de gestion des abonnements (https://manage.visualstudio.com), le processus à suivre est simple.  Toutefois, si votre organisation utilise toujours le Centre de gestion des licences en volume (VLSC), il n’existe aucune fonctionnalité de renvoi automatique de l’e-mail de notification.  

Pour renvoyer un e-mail de notification d’attribution à partir de VLSC, un administrateur doit procéder comme suit :

## <a name="resending-the-assignment-email"></a>Renvoi de l’e-mail d’attribution :

Pour que VLSC puisse générer une nouvelle notification, il est nécessaire de modifier les informations sur l’e-mail de l’abonné une fois, puis de rétablir l’e-mail d’origine sur la même transaction. VLSC réagit alors comme si un nouvel abonnement avait été attribué, et il envoie une nouvelle fois l’e-mail d’attribution.

1.  Accédez au [Centre de gestion des licences en volume (VLSC)](https://www.microsoft.com/Licensing/servicecenter/default.aspx) et connectez-vous.
2.  Cliquez sur l’onglet **Abonnements**, puis sélectionnez **Abonnements Visual Studio**.
3.  Cliquez sur le **numéro de contrat** associé à l’abonnement Visual Studio.
4.  Cliquez sur la flèche vers le bas dans la barre de recherche. 
5.  Recherchez l’abonné à l’aide du champ **Adresse e-mail**.
6.  Recherchez l’abonné dans les résultats de la recherche, puis cliquez sur le nom de famille. 
7.  Cliquez sur **Modifier**.
8.  Apportez une modification à l’abonnement. Par exemple, supprimez un caractère de l’adresse e-mail de l’abonné. Cliquez sur le bouton **Enregistrer**.
9.  Une fois les informations enregistrées, cliquez sur **Modifier**, rétablissez les données que vous venez de modifier, puis cliquez sur **Enregistrer**.  

L’abonnement est alors considéré comme une nouvelle attribution, et l’e-mail de notification d’attribution est renvoyé à l’abonné.  