---
title: "Contrôle VSPackage Architecture source | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control packages, architecture
ms.assetid: 453125fc-23dc-49b1-8476-94581f05e6c7
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80153e271fed6a7fab49e00c8124f1ede7613bfa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-vspackage-architecture"></a>Architecture du contrôle de code source VSPackage
Un package de contrôle de code source est un VSPackage qui utilise des services qui la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE fournit. En retour, un package de contrôle de code source fournit sa fonctionnalité sous la forme d’un service de contrôle de code source. En outre, un package de contrôle de code source est une alternative plus polyvalente que le plug-in pour l’intégration du contrôle de code source dans un contrôle de code source [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Un contrôle de code source du plug-in qui implémente l’API de plug-in de contrôle de Source respecte un contrat strict. Par exemple, un plug-in Impossible de remplacer la valeur par défaut [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l’interface utilisateur (IU). En outre, l’API de plug-in de contrôle de Source n’active pas un plug-in implémenter son propre modèle de contrôle de code source. Un package de contrôle de code source, contourne Toutefois, les deux de ces limitations. Un package de contrôle de code source a un contrôle complet sur l’expérience de contrôle de source de l’un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilisateur. En outre, un package de contrôle de code source peut utiliser son propre modèle de contrôle de code source et la logique, et elle peut définir toutes les interfaces utilisateur liée au contrôle de source.  
  
## <a name="source-control-package-components"></a>Composants de Package de contrôle de code source  
 Comme indiqué dans le diagramme d’architecture, une [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] composant nommé le Stub de contrôle de code Source est un VSPackage qui intègre un package avec un contrôle de code source [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 Stub de contrôle de code source gère les tâches suivantes.  
  
-   Fournit l’interface utilisateur commune qui est requis pour l’inscription du package de contrôle de code source.  
  
-   Charge un package de contrôle de code source.  
  
-   Définit un package de contrôle de code source comme actif/inactif.  
  
 Stub de contrôle de code source recherche le service actif pour le package de contrôle de code source et achemine les entrants de tous les appels de service à partir de l’IDE de ce package.  
  
 Le Package de l’adaptateur de contrôle de Source est un contrôle de code source spécial de package [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fournit. Ce package est un composant central de prise en charge du contrôle plug-ins de code source en fonction de l’API de plug-in de contrôle de Source. Lorsqu’un plug-in de contrôle de code source est actif plug-in, le Stub de contrôle de code Source envoie ses événements pour le Package de l’adaptateur de contrôle Source. À son tour, le Package de l’adaptateur de contrôle Source communique avec le plug-in de contrôle de code source à l’aide de l’API de plug-in de contrôle de Source et fournit également une interface utilisateur commune pour tous les plug-ins de contrôle de code source par défaut.  
  
 Lorsqu’un package de contrôle de code source est le package en cours, en revanche, le Stub de contrôle de Source de communiquer directement avec le package à l’aide de la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] interfaces de Package de contrôle de code Source. Le package de contrôle de code source est chargé d’héberger son propre contrôle de source de l’interface utilisateur.  
  
 ![Graphique d’Architecture du contrôle de code source](../../extensibility/internals/media/vsipsccarch.gif "VSIPSCCArch")  
  
 Pour un package de contrôle de code source, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ne fournit pas de code de contrôle de code source ou à une API pour l’intégration. Ceci contraste avec l’approche décrite dans [création d’un plug-in de contrôle de code Source](../../extensibility/internals/creating-a-source-control-plug-in.md) dans lequel le plug-in de contrôle de code source doit implémenter un ensemble rigid de fonctions et les rappels.  
  
 Comme n’importe quel VSPackage, un package de contrôle de code source est un objet COM qui peut être créé à l’aide de `CoCreateInstance`. Le VSPackage devient disponible pour le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Lorsqu’une instance a été créée, un VSPackage reçoit un pointeur de site et un <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> interface qui fournit l’accès VSPackage pour les services disponibles et les interfaces dans l’IDE.  
  
 L’écriture d’un package de contrôle de code source basé sur le VSPackage nécessite des compétences de programmation plus avancées que l’écriture en fonction des API de plug-in de contrôle de Source de plug-in.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 [Prise en main](../../extensibility/internals/getting-started-with-source-control-vspackages.md)