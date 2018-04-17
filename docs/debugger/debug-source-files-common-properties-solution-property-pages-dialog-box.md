---
title: Déboguer la boîte de dialogue Pages de propriété de Source, propriétés communes, les fichiers Solution | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.options.FindSource
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Debug Source Files property page
- debugging [Visual Studio], specifying source and symbol files
- source files, specifying in debugger
- debugger, source files
ms.assetid: 0af11464-eeb1-4d0b-87a6-0cc96779afb1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec0d60eef17a6ba92a8346ec6c7ea572aea6297e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="debug-source-files-common-properties-solution-property-pages-dialog-box"></a>Fichiers sources pour le débogage, Propriétés communes, boîte de dialogue Pages de propriétés de Solution
Cette page de propriétés spécifie à quel endroit le débogueur recherchera les fichiers sources lors du débogage de la solution.  
  
 Pour accéder à la **déboguer les fichiers sources** page de propriétés, avec le bouton droit sur votre Solution dans **l’Explorateur de solutions** et sélectionnez **propriétés** dans le menu contextuel. Développez le **propriétés communes** dossier, puis cliquez sur le **déboguer les fichiers sources** page.  
  
 **Répertoires contenant du code source**  
 Contient la liste des répertoires dans lesquels le débogueur recherche les fichiers sources lors du débogage de la solution. Les sous-répertoires des dossiers spécifiés sont également récupérés.  
  
 **Ne pas rechercher ces fichiers sources**  
 Entrez le nom des fichiers que vous souhaitez soustraire à la lecture du débogueur. Si le débogueur trouve un de ces fichiers dans un des répertoires spécifiés précédemment, il l'ignore. Si le **rechercher la Source de** boîte de dialogue s’affiche pendant que vous déboguez et que vous cliquez sur **Annuler**, le fichier que vous recherchiez est ajouté à cette liste afin que le débogueur ne continue pas à rechercher ce fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)