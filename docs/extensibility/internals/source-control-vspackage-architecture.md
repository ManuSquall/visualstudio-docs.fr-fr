---
title: Source Control VSPackage Architecture (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705087"
---
# <a name="source-control-vspackage-architecture"></a>Architecture de VSPackage de contrôle de code source
Un package de contrôle des sources est un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSPackage qui utilise les services que l’IDE fournit. En retour, un package de contrôle des sources fournit sa fonctionnalité en tant que service de contrôle source. En outre, un package de contrôle des sources est une alternative plus [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]polyvalente qu’un plug-in de contrôle source pour intégrer le contrôle des sources dans .

 Un plug-in de contrôle source qui met en œuvre l’API de contrôle source respecte un contrat strict. Par exemple, un plug-in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne peut pas remplacer l’interface utilisateur par défaut (interface utilisateur). De plus, l’API de contrôle source ne permet pas à un plug-in de mettre en œuvre son propre modèle de contrôle des sources. Un paquet de contrôle des sources, cependant, surmonte ces deux limitations. Un package de contrôle des sources a un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contrôle complet sur l’expérience de contrôle source d’un utilisateur. En outre, un paquet de contrôle des sources peut utiliser son propre modèle de contrôle source et la logique, et il peut définir toutes les interfaces utilisateur liées au contrôle source.

## <a name="source-control-package-components"></a>Composants de paquets de contrôle des sources
 Comme le montre le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] diagramme d’architecture, un composant nommé le cose de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]contrôle de la source est un VSPackage qui intègre un paquet de contrôle des sources avec .

 Source Control Stub s’occupe des tâches suivantes.

- Fournit l’interface utilisateur commune qui est nécessaire pour l’enregistrement des colis de contrôle des sources.

- Charge un paquet de contrôle des sources.

- Définit un paquet de contrôle des sources en tant qu’actif/inactif.

  Source Control Stub recherche le service actif pour le paquet de contrôle des sources et les itinéraires de tous les appels de service entrants de l’IDE à ce paquet.

  Le paquet d’adaptateur de contrôle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] des sources est un ensemble spécial de contrôle des sources qui fournit. Ce paquet est le composant central pour soutenir les plug-ins de contrôle source basés sur l’API de contrôle source plug-in. Lorsqu’un plug-in de contrôle source est le plug-in actif, le cost de contrôle source envoie ses événements à l’ensemble d’adaptateurs de contrôle des sources. À son tour, le paquet d’adaptateur de contrôle des sources communique avec le plug-in de contrôle source en utilisant l’API plug-in de contrôle source et fournit également une interface utilisateur par défaut qui est commun pour tous les plug-ins de contrôle de source.

  Lorsqu’un paquet de contrôle des sources est le paquet actif, d’autre part, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] le contrôle source Stub communique directement avec le paquet en utilisant les interfaces Source-Control Package. Le paquet source-contrôle est responsable de l’hébergement de son propre interface utilisateur de contrôle source.

  ![Graphique d'architecture de contrôle de code source](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")

  Pour un paquet de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contrôle des sources, ne fournit pas de code de contrôle des sources ou d’une API pour l’intégration. Comparez cela avec l’approche décrite dans [La création d’un plug-in de contrôle source](../../extensibility/internals/creating-a-source-control-plug-in.md) où le plug-in de contrôle source doit implémenter un ensemble rigide de fonctions et de rappels.

  Comme tout VSPackage, un package de contrôle des sources `CoCreateInstance`est un objet COM qui peut être créé en utilisant . Le VSPackage se met [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>disposition de l’IDE en mettant en œuvre . Lorsqu’une instance a été créée, un VSPackage reçoit un pointeur de site et une <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface qui fournit l’accès VSPackage aux services et interfaces disponibles dans l’IDE.

  L’écriture d’un package de contrôle des sources basé sur VSPackage nécessite une expertise de programmation plus avancée que l’écriture d’un plug-in de contrôle source.

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>
- [Prise en main](../../extensibility/internals/getting-started-with-source-control-vspackages.md)
