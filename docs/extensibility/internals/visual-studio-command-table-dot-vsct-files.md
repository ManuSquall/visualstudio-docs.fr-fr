---
title: Visual Studio Command Table (. Fichiers VSCT) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 05c154a7ba87101f4a747b58d1a9ae4de16b7062
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988869"
---
# <a name="visual-studio-command-table-vsct-files"></a>Fichiers Visual Studio Command Table (.Vsct)
Un fichier de configuration de table de commande est un fichier texte qui décrit l’ensemble des commandes qui contient un VSPackage. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] commande les compilateur (VSTC) de table compile les fichiers de configuration XML (fichiers .vsct) en fichiers de sortie (.cto) de table de commande binaire. Les fichiers .cto résultants sont les mêmes que celles qui sont créées en utilisant le compilateur de table (CTC) de commande pour compiler des fichiers de configuration .ctc. Toutefois, les fichiers .vsct basé sur XML a certains avantages, notamment un éditeur XML et le XML IntelliSense.  
  
 Pour en savoir plus sur la syntaxe et la sémantique des fichiers .vsct, consultez [conception XML Command Table (. Fichiers VSCT)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>Dans cette section  
 [Conception de fichiers XML Command Table (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Explique comment concevoir des fichiers .vsct.  
  
 [Guide pratique pour Créer un. Fichier VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Compare les méthodes de création d’un fichier .vsct. Décrit le processus permettant de créer manuellement un nouveau fichier .vsct.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fournit des détails sur chaque section du fichier de configuration XML de table de commandes.  
  
 [Commande de Configuration de la Table (. Fichiers CTC)](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Présente une vue d’ensemble du format de fichier .ctc déconseillées.  
  
 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Décrit la spécification de format de table de commande.  
  
 [Ressources dans VSPackages](../../extensibility/internals/resources-in-vspackages.md)  
 Décrit comment utiliser les ressources non managées et non managées dans les VSPackages gérés.  
  
 [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explique comment créer une interface utilisateur comprenant des menus, des barres d’outils et des listes déroulantes de commandes.