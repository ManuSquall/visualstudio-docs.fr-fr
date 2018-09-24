---
title: Temps de réflexion des tests de charge dans Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 8f8f90eb341112cd700d45b6b7c7d100cad2a024
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39175980"
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Modifier les temps de réflexion pour simuler les délais d’interaction humaine avec un site web dans les scénarios de tests de charge

Les temps de réflexion permettent de simuler un comportement humain selon lequel les utilisateurs attendent entre des interactions avec un site web. Ils ont lieu entre les demandes dans un test de performances web et entre les itérations de test dans un scénario de test de charge. L'utilisation de temps de réflexion dans un test de charge peut être utile pour la création de simulations de charge plus précises. Vous pouvez choisir d'utiliser ou d'ignorer les temps de réflexion dans les tests de charge. Pour activer ou désactiver les temps de réflexion dans vos tests de charge, utilisez **l’Éditeur de test de charge**.

 Le *profil de réflexion* est un paramètre qui s’applique à un scénario dans un test de charge. Le paramètre détermine si les temps de réflexion enregistrés dans les différents tests de performances web sont utilisés pendant le test de charge. Si vous souhaitez utiliser des temps de réflexion dans certains tests de performances web mais pas dans d’autres, placez-les dans des scénarios différents. Pour plus d’informations sur les scénarios, voir [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md).

 La première étape consiste à choisir ou non d’utiliser les temps de réflexion dans un test de charge lors de sa création avec **l’Assistant Nouveau test de charge**. Pour plus d’informations, voir [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md).

 Les options **Profil de réflexion** sont décrites dans la liste suivante :

**Off**

Les temps de réflexion sont ignorés. Utilisez ce paramètre si vous souhaitez générer une charge maximale afin de soumettre votre serveur web à une contrainte importante. Si vous essayez de créer des interactions plus réalistes entre l’utilisateur et un serveur web, ne vous en servez pas.

**On**

Les temps de réflexion sont utilisés exactement tels qu’ils ont été enregistrés dans le test de performances web. Ils simulent plusieurs utilisateurs qui exécutent des tests de performances web. Un test de charge simulant plusieurs utilisateurs, l’utilisation du même temps de réflexion pourrait créer un modèle de charge d’utilisateurs virtuels synchronisés anormal.

**Distribution normale**

Les temps de réflexion sont utilisés, mais varient sur une courbe normale. Fournit une simulation d'utilisateurs virtuels plus réaliste en variant légèrement le temps de réflexion entre les demandes.

> [!NOTE]
> Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés du scénario de test de charge](../test/load-test-scenario-properties.md).

## <a name="change-the-think-profile"></a>Modifier le profil de réflexion

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Pour modifier un profil de réflexion dans un scénario de test de charge

1.  Dans le projet de test de performances web et de charge, ouvrez un test de charge.

2.  Dans **l’éditeur de test de charge**, choisissez le nœud de scénario où vous souhaitez changer le **Profil de réflexion**. Le **Profil de réflexion** s’affiche dans la fenêtre **Propriétés**. Appuyez sur **F4** pour afficher la fenêtre **Propriétés**.

3.  Modifiez la propriété **Profil de réflexion** dans la fenêtre **Propriétés**.

4.  Quand vous avez fini de changer les propriétés, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez ensuite exécuter votre test de charge avec le nouveau profil de réflexion.

## <a name="see-also"></a>Voir aussi

- [Modifier les scénarios de test de charge](../test/edit-load-test-scenarios.md)