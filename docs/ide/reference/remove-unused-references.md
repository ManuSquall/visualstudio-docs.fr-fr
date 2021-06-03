---
title: Supprimer les références inutilisées
description: Découvrez comment nettoyer les références de projet et les packages NuGet qui n’ont pas d’utilisation avec la nouvelle commande supprimer les références inutilisées.
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 707769229ad7bc1864a135bade1df918d4b27847
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352087"
---
# <a name="remove-unused-references"></a>Supprimer les références inutilisées

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Ce qui suit :** Vous permet de supprimer les références inutilisées.

Dans les **cas suivants :** Vous souhaitez nettoyer les références de projet et les packages NuGet qui n’ont pas d’utilisation. 

**Pourquoi :** La suppression de références de projet qui n’ont pas d’utilisation permet d’économiser de l’espace et de réduire le temps de démarrage de votre application, car il faut du temps pour charger chaque module et éviter que les métadonnées de chargement du compilateur ne soient jamais utilisées.

## <a name="how-to"></a>Procédures

1. Cliquez avec le bouton droit sur un nœud nom du projet ou dépendances dans Explorateur de solutions.

2. Sélectionnez **Supprimer les références inutilisées**.

    ![Supprimer les références inutilisées, commande](media/remove-unused-references-command.png)

3. La boîte de dialogue **Supprimer les références inutilisées** s’ouvre et affiche les références qui n’ont pas d’utilisation dans le code source. Les références inutilisées sont présélectionnées en vue de leur suppression avec une option permettant de conserver les références en les sélectionnant `Keep` dans la liste déroulante action.

    ![Boîte de dialogue Supprimer les références inutilisées](media/remove-unused-references-dialog.png)

5. Cliquez `Apply` pour supprimer les références sélectionnées. 

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)