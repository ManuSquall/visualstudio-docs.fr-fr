---
title: Extraire une classe de base
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8c389ac6285b3f20dcdf05833f1ff3202d155c4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962806"
---
# <a name="extract-base-class"></a>Extraire une classe de base

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Extraire la classe de base.

Dans les **cas suivants :** Vous souhaitez extraire les membres d’une classe sélectionnée vers une nouvelle classe de base.

**Pourquoi :** L’extraction manuelle des membres peut prendre du temps et vous sortir de votre flux de travail. 

## <a name="how-to"></a>Procédures

1. Placez le signe insertion sur le nom de la classe ou sur un membre mis en surbrillance.

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

3. Sélectionnez **Tirer le ou les membres jusqu'à la nouvelle classe de base**.

    ![Boîte de dialogue Extraire la classe de base](media/extract-base-class.png)

La boîte de dialogue **Extraire la classe de base** s’ouvre, dans laquelle vous pouvez spécifier le nom de la classe de base et l’emplacement où elle doit être placée. Vous pouvez sélectionner les membres que vous souhaitez transférer vers la nouvelle classe de base et choisir de rendre les membres abstraits en activant la case à cocher dans la colonne créer une colonne abstraite.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
