---
title: "Guide pratique pour le renvoi d’e-mails d’attribution d’abonnements à partir de VLSC | Documents Microsoft"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 12/29/2017
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to a subscriber from within VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 7162435044a578a94249774305f2c6b8b6438219
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-resend-subscription-assignment-emails-from-vlsc"></a>Guide pratique pour le renvoi d’e-mails d’attribution d’abonnements à partir de VLSC :

Quand un abonnement a été attribué à un abonné dans VLSC et que ce dernier demande à recevoir de nouveau l’e-mail d’attribution, vous pouvez le faire en modifiant les informations sur l’adresse e-mail de l’abonné, puis en rétablissant l’adresse d’origine. L’e-mail d’attribution sera alors automatiquement renvoyé à l’abonné.

Suivez les instructions ci-dessous pour renvoyer l’e-mail d’attribution :


1. Accédez au Centre de gestion des licences en volume (VLSC) et connectez-vous.
2. Sur les pages d’administration de VLSC, cliquez sur **Abonnements**, puis sur **Abonnements Visual Studio**.
3. Cliquez sur le **numéro de contrat** associé à l’abonnement Visual Studio.
4. Cliquez sur la flèche vers le bas dans la barre de **recherche**.  
5. Recherchez l’abonné à l’aide du champ Adresse e-mail.
6. Dans la liste des résultats, cliquez sur le **nom** de l’abonné.
7. Cliquez sur **Modifier**.
8. Apportez une modification à l’abonnement. La modification que vous apportez n’a pas d’importance, un simple changement suffit.  Par exemple, supprimez un caractère de l’adresse e-mail de l’abonné (supprimez la lettre « m » de .com). Cliquez sur le bouton **Enregistrer**.
9. Une fois les informations enregistrées, cliquez de nouveau sur le bouton **Modifier** et réinsérez le caractère supprimé de l’adresse e-mail. Cliquez sur **Enregistrer**.
   
VLSC détectera alors que des modifications ont été apportées à l’abonnement et renverra l’e-mail d’attribution à l’adresse indiquée dans le portail. 

> [!NOTE]
> - Les nouveaux abonnements attribués génèrent automatiquement l’adresse e-mail d’attribution. La procédure ci-dessus est uniquement nécessaire quand un utilisateur demande à recevoir une nouvelle notification d’attribution par e-mail ou quand la notification n’est pas envoyée pour une raison quelconque.
> - Elle n’est pas nécessaire pour renvoyer des e-mails d’attribution pour les abonnements attribués via https://manage.visualstudio.com.  Pour renvoyer des e-mails d’attribution aux abonnés dans le portail, sélectionnez simplement les abonnés concernés et cliquez sur le bouton **Renvoyer** en haut de la liste d’abonnés.  