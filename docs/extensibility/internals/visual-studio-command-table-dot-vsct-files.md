---
title: Table de commandes Visual Studio (. Fichiers vsct) | Microsoft Docs
description: En savoir plus sur les fichiers de configuration de table de commandes, qui sont des fichiers texte qui décrivent l’ensemble de commandes contenu dans un VSPackage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 377bae52f506c1cb9ac0f6b2d4136faaab0b50ad
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488035"
---
# <a name="visual-studio-command-table-vsct-files"></a>Fichiers Visual Studio Command Table (.Vsct)
Un fichier de configuration de table de commandes est un fichier texte qui décrit l’ensemble de commandes contenu dans un VSPackage. Le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilateur de table de commandes (vsct) compile les fichiers de configuration XML (fichiers. vsct) en fichiers de sortie de table de commandes binaires (. directeur). Les fichiers. directeur technique résultants sont les mêmes que ceux créés à l’aide du compilateur de table de commandes (CTC) pour compiler les fichiers de configuration. CTC. Toutefois, les fichiers. vsct basés sur XML présentent certains avantages, tels qu’un éditeur XML et XML IntelliSense.

 Pour en savoir plus sur la syntaxe et la sémantique des fichiers. vsct, consultez conception d’une [table de commandes XML (. Fichiers vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>Dans cette section
 [Conception de fichiers XML Command Table (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Décrit comment concevoir des fichiers. vsct.

 [Guide pratique pour créer un fichier .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Compare les méthodes de création d’un fichier. vsct. Décrit le processus de création manuelle d’un nouveau fichier. vsct.

## <a name="related-sections"></a>Sections connexes
 [Schéma de référence XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Fournit des détails sur chaque section du fichier de configuration XML de la table de commandes.

 [Configuration de la table de commandes (. CTC)](/previous-versions/bb165153(v=vs.100)) présente une vue d’ensemble du format de fichier. CTC déconseillé.

 [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Décrit la spécification de format de la table de commandes.

 [Ressources dans VSPackages](../../extensibility/internals/resources-in-vspackages.md)

 Décrit comment utiliser des ressources managées et non managées dans des VSPackages managés.

 [Commandes, menus et barres d’outils](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explique comment créer une interface utilisateur comprenant des menus, des barres d’outils et des listes déroulantes de commandes.