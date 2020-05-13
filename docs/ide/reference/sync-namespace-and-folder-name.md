---
title: Synchronisation de l’espace de noms et du nom du dossier
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: d7073edaf6ecc261c58bf1e5607323b9214c5ed0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "67160755"
---
# <a name="sync-namespace-and-folder-name"></a>Synchronisation de l’espace de noms et du nom du dossier

Cette refactorisation s’applique à :

- C#

**Quoi :** Synchronisez l’espace de nom et le nom du dossier.

**Quand :** Vous souhaitez réarchiler des parties de votre solution en faisant glisser un fichier vers un nouveau dossier. 

**Pourquoi:** Vous voulez vous assurer que votre espace de nom se tient au courant de votre nouvelle structure de dossier.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans l’espace de noms.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Modifier espace de noms en \<nom du dossier>**.

   ![Synchronisation de l’espace de noms et du nom du dossier](media/sync-namespace-and-folder-name.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
