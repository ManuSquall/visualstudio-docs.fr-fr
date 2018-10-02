---
title: Architecture de VSPackage de contrôle source | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d2a76a877581085b6bdffd8522bfcea24ea9e24
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494849"
---
# <a name="source-control-vspackage-architecture"></a>Architecture de VSPackage de contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Architecture de VSPackage de contrôle de Source](https://docs.microsoft.com/visualstudio/extensibility/internals/source-control-vspackage-architecture).  
  
Un package de contrôle de code source est un VSPackage qui utilise des services qui la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit de l’IDE. En retour, un package de contrôle de code source fournit ses fonctionnalités comme un service de contrôle de code source. En outre, un package de contrôle de code source est une alternative plus polyvalente que le plug-in pour l’intégration du contrôle de code source dans un contrôle de code source [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Un plug-in qui implémente l’API de plug-in de contrôle de Source de contrôle de code source respecte un contrat strict. Par exemple, un plug-in Impossible de remplacer la valeur par défaut [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] l’interface utilisateur (IU). En outre, l’API de plug-in de contrôle de Source ne permet pas un plug-in implémenter son propre modèle de contrôle de code source. Un package de contrôle de code source, surmonte Toutefois, ces deux restrictions. Un package de contrôle de code source a contrôle complet sur l’expérience de contrôle de source d’un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] utilisateur. En outre, un package de contrôle de code source peut utiliser son propre modèle de contrôle source et la logique, et elle peut définir toutes les interfaces utilisateur relatifs au contrôle de source.  
  
## <a name="source-control-package-components"></a>Composants de Package de contrôle de code source  
 Comme indiqué dans le diagramme d’architecture, un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] composant nommé le Stub de contrôle de Source est un VSPackage qui s’intègre à un package de contrôle de code source avec [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Stub de contrôle de code source gère les tâches suivantes.  
  
-   Fournit l’interface utilisateur commune qui est nécessaire pour l’inscription de package de contrôle de code source.  
  
-   Charge un package de contrôle de code source.  
  
-   Définit un package de contrôle de code source comme actives/inactives.  
  
 Stub de contrôle de source recherche le service actif pour le package de contrôle de code source et achemine les appels de service tout trafic entrant à partir de l’IDE pour ce package.  
  
 Le Package de l’adaptateur de contrôle de code Source est un contrôle de code source spéciaux package [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit. Ce package est un composant central de prise en charge de la source plug-ins de contrôle basés sur l’API de plug-in de contrôle Source. Lorsqu’un plug-in de contrôle de code source est actif plug-in, le Stub de contrôle Source envoie ses événements pour le Package de l’adaptateur de contrôle de code Source. À son tour, le Package de l’adaptateur de contrôle de code Source communique avec le plug-in de contrôle de code source à l’aide de l’API de plug-in de contrôle de Source et fournit également une interface utilisateur commune pour tous les plug-ins de contrôle de code source par défaut.  
  
 Lorsqu’un package de contrôle de code source est le package actif, quant à eux, le Stub de contrôle Source communique directement avec le package à l’aide de la [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] interfaces de Package de contrôle de code Source. Le package de contrôle de code source est chargé d’héberger son propre contrôle de source de l’interface utilisateur.  
  
 ![Graphique d’Architecture du contrôle de code source](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Pour un package de contrôle de code source, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ne fournit pas de code de contrôle de source ou une API pour l’intégration. Comparez ceci avec l’approche décrite dans [création d’un plug-in de contrôle de Source](../../extensibility/internals/creating-a-source-control-plug-in.md) dans lequel le plug-in de contrôle de code source doit implémenter un ensemble rigid de fonctions et les rappels.  
  
 Comme n’importe quel package Visual Studio, un package de contrôle de code source est un objet COM qui peut être créé à l’aide de `CoCreateInstance`. Le VSPackage devient disponible pour le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Lorsqu’une instance a été créée, un VSPackage reçoit un pointeur de site et un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface qui fournit l’accès de package Visual Studio pour les services disponibles et les interfaces dans l’IDE.  
  
 Écriture d’un package de contrôle de code source basé sur un VSPackage nécessite des compétences de programmation plus avancées que l’écriture basée sur une API de plug-in de contrôle de Source de plug-in.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Prise en main](../../extensibility/internals/getting-started-with-source-control-vspackages.md)

