---
title: Tâche XSD | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (Visual C++))
- MSBuild (Visual C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e83f21ab05e298635c13f8e2bddb72520459ab1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56631170"
---
# <a name="xsd-task"></a>XSD (tâche)
Inclut dans un wrapper l’outil Définition de schéma XML (*xsd.exe*), qui génère des fichiers de schéma ou de classe à partir d’une source.

> [!NOTE]
> Dans Visual Studio 2017, *xsd.exe* n’est plus pris en charge par les projets C++. Vous pouvez toujours utiliser les API **Microsoft.VisualC.CppCodeProvider** en ajoutant manuellement *CppCodeProvider.dll* au GAC.

## <a name="parameters"></a>Paramètres
 Le tableau ci-dessous décrit les paramètres de la tâche **XSD**.

-   **AdditionalOptions**

     Paramètre **String** facultatif.

     Liste des options comme indiqué sur la ligne de commande. Par exemple, /\<option1> /\<option2> /\<option#>. Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **XSD**.

-   **GenerateFromSchema**

     Paramètre **String** facultatif.

     Indique les types qui sont générés à partir du schéma spécifié.

     Spécifiez l’une des valeurs suivantes, chacune d’elles correspondant à une option XSD.

    -   **classes** - **/classes**

    -   **dataset** - **/dataset**

-   **Language**

     Paramètre **String** facultatif.

     Spécifie le langage de programmation à utiliser pour le code généré.

     Vous avez le choix entre **CS** (C#, qui est la valeur par défaut), **VB** (Visual Basic) ou **JS** (JScript). Vous pouvez également spécifier un nom qualifié complet pour une classe qui implémente `System.CodeDom.Compiler.CodeDomProvider Class`.

-   **Namespace**

     Paramètre **String** facultatif.

     Spécifie l'espace de noms du runtime pour les types générés.

-   **Sources**

     Paramètre `ITaskItem[]` requis.

     Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.

-   **SuppressStartupBanner**

     Paramètre **Boolean** facultatif.

     Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.

-   **TrackerLogDirectory**

     Paramètre **String** facultatif.

     Spécifie le répertoire du journal de Tracker.

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)