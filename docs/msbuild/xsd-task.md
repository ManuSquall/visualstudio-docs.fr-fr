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
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31c256e02901d4f7dd7de6f14e9f650626feac25
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565784"
---
# <a name="xsd-task"></a>XSD (tâche)
Inclut dans un wrapper l’outil Définition de schéma XML (*xsd.exe*), qui génère des fichiers de schéma ou de classe à partir d’une source.

> [!NOTE]
> À partir de Visual Studio 2017, *xsd.exe* n’est plus pris en charge par les projets C++. Vous pouvez toujours utiliser les API **Microsoft.VisualC.CppCodeProvider** en ajoutant manuellement *CppCodeProvider.dll* au GAC.

## <a name="parameters"></a>Parameters
 Le tableau ci-dessous décrit les paramètres de la tâche **XSD**.

- **AdditionalOptions**

     Paramètre de **chaîne** facultatif.

     Liste des options comme indiqué sur la ligne de commande. Par exemple, /\<option1> /\<option2> /\<option#>. Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **XSD**.

- **GenerateFromSchema**

  Paramètre de **chaîne** facultatif.

  Indique les types qui sont générés à partir du schéma spécifié.

  Spécifiez l’une des valeurs suivantes, chacune d’elles correspondant à une option XSD.

  - **classes** -  **/classes**

  - **dataset** -  **/dataset**

- **Langue**

     Paramètre de **chaîne** facultatif.

     Spécifie le langage de programmation à utiliser pour le code généré.

     Vous avez le choix entre **CS** (C#, qui est la valeur par défaut), **VB** (Visual Basic) ou **JS** (JScript). Vous pouvez également spécifier un nom qualifié complet pour une classe qui implémente `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Namespace**

     Paramètre de **chaîne** facultatif.

     Spécifie l'espace de noms du runtime pour les types générés.

- **Sources**

     Paramètre `ITaskItem[]` requis.

     Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.

- **SuppressStartupBanner**

     Paramètre **Boolean** facultatif.

     Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.

- **TrackerLogDirectory**

     Paramètre de **chaîne** facultatif.

     Spécifie le répertoire du journal de Tracker.

## <a name="see-also"></a>Voir aussi
- [Informations de référence sur les tâches](../msbuild/msbuild-task-reference.md)
