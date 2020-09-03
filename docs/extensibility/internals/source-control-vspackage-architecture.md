---
title: Architecture du VSPackage de contrôle de code source | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6e62aa9e2d725e982f0605e2721f0bfeb3cc5ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705087"
---
# <a name="source-control-vspackage-architecture"></a>Architecture de VSPackage de contrôle de code source
Un package de contrôle de code source est un VSPackage qui utilise des services fournis par l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. En retour, un package de contrôle de code source fournit ses fonctionnalités comme un service de contrôle de code source. En outre, un package de contrôle de code source est une alternative plus polyvalente qu’un plug-in de contrôle de code source pour intégrer le contrôle de code source dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Un plug-in de contrôle de code source qui implémente l’API de plug-in de contrôle de code source respecte un contrat strict. Par exemple, un plug-in ne peut pas remplacer l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface utilisateur par défaut. En outre, l’API de plug-in de contrôle de code source n’autorise pas un plug-in à implémenter son propre modèle de contrôle de code source. Toutefois, un package de contrôle de code source présente ces deux limitations. Un package de contrôle de code source dispose d’un contrôle total sur l’expérience de contrôle de code source d’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisateur. En outre, un package de contrôle de code source peut utiliser son propre modèle de contrôle de code source et sa propre logique, et il peut définir toutes les interfaces utilisateur liées au contrôle de code source.

## <a name="source-control-package-components"></a>Composants de package de contrôle de code source
 Comme indiqué dans le diagramme d’architecture, un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composant nommé stub de contrôle de code source est un VSPackage qui intègre un package de contrôle de code source avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 Le stub de contrôle de code source gère les tâches suivantes.

- Fournit l’interface utilisateur commune requise pour l’inscription du package de contrôle de code source.

- Charge un package de contrôle de code source.

- Définit un package de contrôle de code source comme actif/inactif.

  Le stub de contrôle de code source recherche le service actif pour le package de contrôle de code source et achemine tous les appels de service entrants de l’IDE vers ce package.

  Le package d’adaptateurs de contrôle de code source est un package de contrôle de code source spécial qui [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit. Ce package est le composant central pour la prise en charge des plug-ins de contrôle de code source basés sur l’API de plug-in de contrôle de code source. Lorsqu’un plug-in de contrôle de code source est le plug-in actif, le stub de contrôle de code source envoie ses événements au package de l’adaptateur de contrôle de code source. À son tour, le package de l’adaptateur de contrôle de code source communique avec le plug-in de contrôle de code source à l’aide de l’API de plug-in de contrôle de code source et fournit également une interface utilisateur par défaut qui est commune à tous les plug-ins de contrôle de code source.

  En revanche, lorsqu’un package de contrôle de code source est le package actif, le stub de contrôle de code source communique directement avec le package à l’aide des [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces de package de contrôle de code source. Le package de contrôle de code source est chargé d’héberger sa propre interface utilisateur de contrôle de code source.

  ![Graphique d'architecture de contrôle de code source](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Pour un package de contrôle de code source, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne fournit pas le code de contrôle de code source ou une API pour l’intégration. Comparez ceci avec l’approche décrite dans [création d’un plug-in de contrôle de code source](../../extensibility/internals/creating-a-source-control-plug-in.md) où le plug-in de contrôle de code source doit implémenter un ensemble rigide de fonctions et de rappels.

  Comme tout VSPackage, un package de contrôle de code source est un objet COM qui peut être créé à l’aide de `CoCreateInstance` . Le VSPackage se met à la disposition de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Lorsqu’une instance de est créée, un VSPackage reçoit un pointeur de site et une <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface qui fournit l’accès VSPackage aux services et interfaces disponibles dans l’IDE.

  L’écriture d’un package de contrôle de code source basé sur VSPackage nécessite une expérience de programmation plus avancée que l’écriture d’un plug-in basé sur une API de plug-in de contrôle de code source.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Prise en main](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
