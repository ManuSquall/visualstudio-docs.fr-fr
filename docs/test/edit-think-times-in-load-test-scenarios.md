---
title: Temps de réflexion des tests de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, think times
- load tests, adding delays
- load tests, changing think times
ms.assetid: 8e03bee5-ab7b-4b40-9497-9dbe91ccb90e
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: cccf2961ceb5abecb33396433e344015143503bf
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2018
---
# <a name="edit-think-times-to-simulate-website-human-interaction-delays-in-load-tests-scenarios"></a>Modifier les temps de réflexion pour simuler les retards d’interaction humaine avec un site web dans les scénarios de tests de charge

Les temps de réflexion permettent de simuler un comportement humain selon lequel les utilisateurs attendent entre des interactions avec un site web. Les temps de réflexion ont lieu entre les requêtes dans un test de performances de site web et entre les itérations de test dans un scénario de test de charge. L'utilisation de temps de réflexion dans un test de charge peut être utile pour la création de simulations de charge plus précises. Vous pouvez choisir d'utiliser ou d'ignorer les temps de réflexion dans les tests de charge. Vous pouvez ensuite désactiver l'utilisation des temps de réflexion dans vos tests de charge dans l'Éditeur de test de charge.

 Le *profil de réflexion* est un paramètre qui s’applique à un scénario dans un test de charge. Le paramètre détermine si les temps de réflexion enregistrés dans chaque test de performances de site web sont utilisés pendant le test de charge. Si vous souhaitez utiliser des temps de réflexion dans certains tests de performances de site web mais pas dans d'autres, vous devez les placer dans des scénarios différents. Pour plus d’informations sur les scénarios, consultez [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md).

 Initialement, vous activez l'utilisation des temps de réflexion dans vos tests de charge lorsque vous créez le test de charge à l'aide de l'Assistant Nouveau test de charge. Pour plus d’informations, consultez [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md).

 Les options de la propriété Profil de réflexion sont décrites dans la liste suivante :

**Off**

Les temps de réflexion sont ignorés. Utilisez ce paramètre lorsque vous souhaitez générer une charge maximale afin de soumettre votre serveur web à une contrainte importante. Ne l’utilisez pas lorsque vous essayez de créer des interactions utilisateur plus réalistes avec un serveur web.

**On**

Les temps de réflexion sont utilisés exactement tels qu'ils ont été enregistrés dans le test de performances de site web. Simule plusieurs utilisateurs qui exécutent les tests de performances de site web exactement comme enregistrés. Un test de charge simulant plusieurs utilisateurs, l’utilisation du même temps de réflexion pourrait créer un modèle de charge d’utilisateurs virtuels synchronisés anormal.

**Distribution normale**

Les temps de réflexion sont utilisés, mais varient sur une courbe normale. Fournit une simulation d'utilisateurs virtuels plus réaliste en variant légèrement le temps de réflexion entre les demandes.

> [!NOTE]
> Pour obtenir une liste complète des propriétés des scénarios de test de charge et leurs descriptions, consultez [Propriétés des scénarios de test de charge](../test/load-test-scenario-properties.md).

## <a name="changing-the-think-profile"></a>Modification du profil de réflexion

### <a name="to-change-a-think-profile-in-a-load-test-scenario"></a>Pour modifier un profil de réflexion dans un scénario de test de charge

1.  Depuis le projet de test de performances Web et de charge, ouvrez un test de charge.

2.  Dans **l’éditeur de test de charge**, choisissez le nœud de scénario où vous souhaitez changer le **Profil de réflexion**. Le **Profil de réflexion** s’affiche dans la fenêtre Propriétés. Appuyez sur F4 pour afficher la fenêtre Propriétés.

3.  Changez la propriété **Profil de réflexion** dans la fenêtre Propriétés.

4.  Après avoir fini de changer les propriétés, choisissez **Enregistrer** dans le menu **Fichier**. Vous pouvez ensuite exécuter votre test de charge avec le nouveau profil de réflexion.

## <a name="see-also"></a>Voir aussi

- [Modification des scénarios de test de charge](../test/edit-load-test-scenarios.md)