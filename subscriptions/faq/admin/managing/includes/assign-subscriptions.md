---
title: Comment attribuer des abonnements Visual Studio ?
description: Vous pouvez attribuer des abonnements à vos utilisateurs finaux un par un ou à l’aide de la fonctionnalité Ajout en bloc afin de charger rapidement et facilement un plus grand...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 09/30/2020
ms.openlocfilehash: add0bac2a9e7eb053c183d66fcee17c8133bb921
ms.sourcegitcommit: ea3c985a23851b424127f2205f617446b6536578
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91642203"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>Comment attribuer des abonnements Visual Studio ?

Vous pouvez attribuer des abonnements à vos utilisateurs finaux un par un ou à l’aide de la fonctionnalité Ajout en bloc afin de charger rapidement et facilement un plus grand nombre d’abonnés à la fois.

Pour attribuer des abonnements individuellement :

1. Sélectionnez l’[onglet Gérer les abonnés](https://manage.visualstudio.com/subscribers) en haut de la page sur [manage.visualstudio.com](https://manage.visualstudio.com).
2. Sélectionnez Ajouter et tapez le nom et l’adresse e-mail de l’utilisateur auquel vous souhaitez attribuer un abonnement.
    1. Si votre organisation utilise Azure Active Directory, le champ du nom propose des personnes figurant dans votre annuaire actuel. Vous pouvez effectuer votre choix dans les résultats de la recherche ou ajouter une personne manuellement.
3. Si vous souhaitez autoriser l’abonné à accéder aux téléchargements de logiciels quand il se connecte au [portail des abonnements Visual Studio](https://my.visualstudio.com/), laissez la case Téléchargements cochée dans la section Paramètres de téléchargement.
4. Complétez la section Préférences de communication afin que nous sachions dans quelle langue envoyer l’e-mail d’affectation à vos abonnés.
5. Si vous souhaitez ajouter des notes associées à l’affectation, utilisez la section Référence.
6. Sélectionnez Ajouter en bas du panneau volant pour terminer l’affectation de votre abonnement. Votre abonné recevra un e-mail et pourra commencer à utiliser son abonnement Visual Studio immédiatement (aucune activation n’est nécessaire de la part de votre abonné).

Pour attribuer des abonnements en bloc :

1. Sélectionnez l’[onglet Gérer les abonnés](https://manage.visualstudio.com/subscribers) en haut de la page sur [manage.visualstudio.com](https://manage.visualstudio.com).
2. Sélectionnez Ajout en bloc, téléchargez le modèle Excel et enregistrez une copie locale.
3. Tous les champs sont obligatoires, à l’exception du champ Référence.
    1. Vérifiez que les champs de formulaire ne contiennent pas de virgules.
    2. Supprimez les espaces avant et après les champs de formulaire.
    3. Assurez-vous que les noms ne contiennent pas d’espace superflu dans les noms ou prénoms composés (par exemple, si une personne porte le prénom composé « Maggie May », il doit être entré sous la forme « MaggieMay »).
4. Revenez à [manage.visualstudio.com](https://manage.visualstudio.com), sélectionnez Ajout en bloc, puis chargez votre copie enregistrée du modèle Excel.
5. Une fois le chargement terminé, une page de confirmation s’affiche et votre liste d’abonnés est renseignée avec vos nouveaux abonnés. Vos abonnés recevront un e-mail et pourront commencer à utiliser leur abonnement Visual Studio immédiatement (aucune activation n’est nécessaire de la part de vos abonnés).

[Pour en savoir plus](https://docs.microsoft.com/visualstudio/subscriptions/assign-license#add-a-single-subscriber) sur la façon d’attribuer des abonnements rapidement et facilement, consultez la documentation sur l’affectation d’abonnements dans le portail d’administration des abonnements Visual Studio.  [Découvrez-en plus](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) sur la gestion des abonnements Visual Studio avec GitHub Enterprise. 

## <a name="what-is-the-github-enterprise-setup-process"></a>Qu’est-ce que le processus d’installation de GitHub Enterprise ? 

GitHub Enterprise est configuré et géré séparément des abonnements Visual Studio. Suite à un achat Visual Studio avec GitHub Enterprise, un processus de configuration d’un compte GitHub Enterprise est lancé en parallèle (mais séparément) de l’établissement d’un contrat dans manage.visualstudio.com. La création de ce compte GitHub Enterprise peut prendre un certain temps.  

Une fois que votre société a configuré un compte GitHub Enterprise, les abonnés à qui ont été attribués des abonnements Visual Studio avec GitHub Enterprise reçoivent un e-mail de GitHub les notifiant que leurs abonnements Visual Studio ont été liés. Une fois que les abonnés ont reçu cet e-mail, ils peuvent contacter leur administrateur d’organisation GitHub pour recevoir une invitation à l’organisation appropriée. 

[Découvrez-en plus](https://docs.microsoft.com/visualstudio/subscriptions/assign-github) sur la gestion des abonnements Visual Studio avec GitHub Enterprise. Pour plus d’informations sur le processus de configuration de GitHub Enterprise, consultez la [documentation sur les abonnés](https://docs.microsoft.com/visualstudio/subscriptions/access-github). 