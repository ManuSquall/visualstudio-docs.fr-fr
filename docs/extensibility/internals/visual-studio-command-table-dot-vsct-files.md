---
title: Tableau de commandes de Visual Studio (. Fichiers VSCT) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71a202bdb71469e4d6b46eb537147092b1ea9013
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-command-table-vsct-files"></a>Tableau de commandes de Visual Studio (. Fichiers VSCT)
Un fichier de configuration de table de commande est un fichier texte qui décrit l’ensemble des commandes contenant un VSPackage. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] commande compilateur de table (VSTC) compile des fichiers de configuration XML (fichiers .vsct) en fichiers de sortie (.cto) de table de commande binary. Les fichiers .cto résultants sont les mêmes que celles qui sont créées en utilisant le compilateur de table (CTC) de commande pour compiler des fichiers de configuration .ctc. Toutefois, les fichiers .vsct de basé sur XML a certains avantages, notamment un éditeur XML et le XML IntelliSense.  
  
 Pour en savoir plus sur la syntaxe et la sémantique des fichiers .vsct, consultez [conception d’une Table de commande XML (. Fichiers VSCT)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>Dans cette section  
 [Conception de fichiers XML Command Table (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Explique comment concevoir des fichiers .vsct.  
  
 [Guide pratique pour créer un fichier .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Compare les méthodes de création d’un fichier .vsct. Décrit le processus de création manuelle d’un nouveau fichier .vsct.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fournit des détails sur chaque section du fichier de configuration XML de table de commande.  
  
 [Configuration de la Table de commandes (. Fichiers CTC)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Présente une vue d’ensemble du format de fichier .ctc déconseillées.  
  
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Décrit la spécification de format de table de commande.  
  
 [Ressources dans VSPackages](../../extensibility/internals/resources-in-vspackages.md)  
 Décrit comment utiliser les ressources non managées et non managées dans les VSPackages gérés.  
  
 [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explique comment créer une interface utilisateur comprenant des menus, des barres d’outils et des listes déroulantes de commandes.