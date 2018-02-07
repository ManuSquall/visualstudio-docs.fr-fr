---
title: "Renommer un nom de fichier pour correspondre à un type C# dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ada7044ebb6718dc0380b387a130ea7b2334e443
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-c"></a>Synchroniser un type en nom de fichier ou un nom de fichier en type dans C# #

<!-- VERSIONLESS -->
**Cette fonctionnalité est disponible dans Visual Studio 2017 et ultérieur.  En outre, les projets .NET Standard ne sont pas encore pris en charge pour cette refactorisation.**

**Quoi :** vous permet de renommer un type pour qu’il corresponde au nom de fichier, ou de renommer un nom de fichier afin qu’il corresponde au type qu’il contient.

**Quand :** vous avez renommé un fichier ou un type et n’avez pas encore mis à jour le fichier ou type correspondant. 

**Pourquoi :** si vous placez un type dans un fichier avec un autre nom, ou vice versa, il est difficile de trouver ce que vous cherchez.  En renommant le type ou le nom de fichier, le code devient plus lisible, ce qui facilite la navigation.

**Comment :**

1. Mettez en surbrillance ou placez le curseur de texte dans le nom du type à synchroniser :

   ![Code mis en surbrillance](media/synctype-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Renommer le fichier en *TypeName*.cs** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Renommer le type en _Filename_.vb** dans la fenêtre contextuelle d’aperçu, où *Filename* est le nom du fichier actuel.
   * **Souris**
     * Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Renommer le fichier en *TypeName*.cs** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.
     * Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Renommer le type en _Filename_.vb** dans la fenêtre contextuelle d’aperçu, où *Filename* est le nom du fichier actuel.

   Le type ou le fichier sera renommé instantanément.  Dans l’exemple ci-dessous, le fichier **MyClass.cs** a été renommé **MyNewClass.cs** afin de correspondre au nom du type.

   ![Résultat de l’action Inclure](media/synctype-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)
