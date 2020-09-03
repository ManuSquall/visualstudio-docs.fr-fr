---
title: Tâche XSD | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0c9dcc0d09887cacca7e6cdaa2e4f2b719c6451c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67826246"
---
# <a name="xsd-task"></a>Tâche XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Encapsule l’outil Définition du schéma XML (xsd.exe), qui génère des fichiers de schéma ou de classe à partir d’une source.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche **XSD**.  
  
- **AdditionalOptions**  
  
     Paramètre de **chaîne** facultatif.  
  
     Liste des options comme indiqué sur la ligne de commande. Par exemple, «*/option1/option2/option #*». Utilisez ce paramètre pour spécifier des options qui ne sont pas représentées par un autre paramètre de tâche **XSD**.  
  
- **GenerateFromSchema**  
  
  Paramètre de **chaîne** facultatif.  

  Indique les types qui sont générés à partir du schéma spécifié.  

  Spécifiez l’une des valeurs suivantes, chacune d’elles correspondant à une option XSD.  

  - **classes**  -  **/classes**  

  - **jeu de données**  -  **/DataSet**  
  
- **Langage**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le langage de programmation à utiliser pour le code généré.  
  
     Vous avez le choix entre **CS** (C#, qui est la valeur par défaut), **VB** (Visual Basic) ou **JS** (JScript). Vous pouvez également spécifier un nom qualifié complet pour une classe qui implémente `System.CodeDom.Compiler.CodeDomProvider Class`.  
  
- **Espace de noms**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie l'espace de noms du runtime pour les types générés.  
  
- **Sources**  
  
     Paramètre `ITaskItem[]` requis.  
  
     Définit un tableau d’éléments de fichier source MSBuild pouvant être consommés et émis par des tâches.  
  
- **SuppressStartupBanner**  
  
     Paramètre **booléen** facultatif.  
  
     Si la valeur est `true`, empêche l'affichage du message de copyright et de numéro de version quand la tâche démarre.  
  
- **TrackerLogDirectory**  
  
     Paramètre de **chaîne** facultatif.  
  
     Spécifie le répertoire du journal de Tracker.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de tâche](../msbuild/msbuild-task-reference.md)
