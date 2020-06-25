---
title: Générer un champ privé et une propriété à partir d’un constructeur
ms.date: 06/20/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 56bd361d2bffb4ff17b03ac6743837032d1934e1
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283721"
---
# <a name="generate-private-field-and-property-from-constructor"></a>Générer un champ privé et une propriété à partir d’un constructeur

Cette refactorisation s’applique à : 

- C# 

**Ce qui suit :** Générez un champ ou une propriété privé à partir d’un constructeur. 

Dans les **cas suivants :** Vous souhaitez ajouter et initialiser rapidement un champ ou une propriété privé à partir d’un constructeur.

**Pourquoi :** L’écriture de champs et de propriétés privés peut être longue et répétitive. L’utilisation de cette refactorisation est rapide et rend le programme plus robuste.

## <a name="how-to"></a>Procédures 

1. Placez le curseur sur le nom du paramètre dans le constructeur.

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
   
3. Sélectionnez ensuite l’une des options suivantes :

- **Créez et initialisez le champ** ou **créez et initialisez la propriété**.

   ![Générer un champ privé à partir d’un constructeur](media/generate-private-field-from-constructor.png)

## <a name="see-also"></a>Voir aussi 

- [Refactorisation](../refactoring-in-visual-studio.md)
