---
title: Générer un champ privé et une propriété à partir d’un constructeur
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour générer un champ privé ou une propriété à partir d’un constructeur.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e989efed8b58746312ed5f5a510efa049393f3db
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617459"
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
