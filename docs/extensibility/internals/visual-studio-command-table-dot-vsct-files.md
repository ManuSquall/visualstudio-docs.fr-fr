---
title: Table de commande de studio visuel (. Vsct) Fichiers (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704026"
---
# <a name="visual-studio-command-table-vsct-files"></a>Fichiers Visual Studio Command Table (.Vsct)
Un fichier de configuration de table de commande est un fichier texte qui décrit l’ensemble des commandes qu’un VSPackage contient. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilateur de table de commande (VSCT) compile les fichiers de configuration basés sur XML (.fichiers de vsct) dans les fichiers de sortie de table de commande binaire (.cto). Les fichiers .cto qui en résultent sont les mêmes que ceux qui sont créés en utilisant le compilateur de table de commande (CTC) pour compiler des fichiers de configuration .ctc. Cependant, les fichiers .vsct basés sur XML ont certains avantages, tels qu’un éditeur XML et XML IntelliSense.

 Pour en savoir plus sur la syntaxe et la sémantique des fichiers .vsct, voir [Designing XML Command Table (. Vsct) Fichiers](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>Dans cette section
 [Conception de fichiers XML Command Table (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Décrit comment concevoir des fichiers .vsct.

 [Guide pratique pour créer un fichier .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Compare les méthodes pour créer un fichier .vsct. Décrit le processus de création manuelle d’un nouveau fichier .vsct.

## <a name="related-sections"></a>Sections connexes
 [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Fournit des détails sur chaque section du fichier de configuration XML du tableau de commande.

 [Configuration de table de commande (. Ctc) Les fichiers](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) présente un aperçu du format de fichier .ctc déprécié.

 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Décrit les spécifications de format de tableau de commande.

 [Ressources dans VSPackages](../../extensibility/internals/resources-in-vspackages.md)

 Décrit comment utiliser les ressources gérées et non gérées dans les VSPackages gérés.

 [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explique comment créer une interface utilisateur comprenant des menus, des barres d’outils et des listes déroulantes de commandes.
