---
title: "Comment renvoyer des e-mails d’affectation d’abonnements à partir de Manage.visualstudio.com ou VLSC | Microsoft Docs"
Author: evanwindom
Ms.author: jaunger
Manager: evelynp
Ms.date: 2/13/2018
Ms.topic: Get-Started-Article
Description: Learn how to resend the subscription assignment to subscribers from manage.visualstudio.com or VLSC
Ms.prod: vs-subscription
Ms.technology: vs-subscriptions
Searchscope: VS Subscription
ms.openlocfilehash: 0ba7d6e36c25ced78b0c6b25688e5eb5b26eb04a
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="how-to-resend-subscription-assignment-emails"></a>Comment renvoyer des e-mails d’affectation d’abonnements :

Les étapes nécessaires pour renvoyer un e-mail d’affectation varient selon le portail utilisé pour gérer vos abonnements. 

## <a name="resending-assignment-emails-from-within-managevisualstudiocom"></a>Renvoi des e-mails d’affectation à partir de manage.visualstudio.com

Le processus de renvoi des e-mails d’affectation à partir du portail manage.visualstudio.com est très simple :

1. Visitez le portail [manage.visualstudio.com](https://manage.visualstudio.com) et connectez-vous. 
2. Utilisez l’onglet **Filtre** pour rechercher l’abonné à qui vous voulez renvoyer l’e-mail d’affectation. (Pour plus d’informations sur le filtrage, consultez [Rechercher un abonnement](/visualstudio/subscriptions/search-license).)
3. Cliquez sur le ou les abonnés.  Vous pouvez utiliser Ctrl + clic ou MAJ + clic pour sélectionner plusieurs abonnés.
4. Cliquez sur **Renvoyer** en haut des résultats de recherche.  

## <a name="resending-assignment-emails-from-within-vlsc"></a>Renvoi des e-mails d’affectation à partir de VLSC
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
