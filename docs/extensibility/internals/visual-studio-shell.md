---
title: Visual Studio Shell - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704003"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
La [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] coquille est le principal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]agent d’intégration dans . La coque fournit les fonctionnalités nécessaires pour permettre à VSPackages de partager des services communs. Parce que l’objectif architectural est de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vest fonctionnalité primaire dans les VSPackages, la coquille est un cadre pour fournir des fonctionnalités de base et de soutenir la communication croisée entre ses composants VSPackages.

## <a name="shell-responsibilities"></a>Responsabilités Shell
 La coquille a les responsabilités clés suivantes :

- Soutenir (via les interfaces COM) les éléments de base de l’interface utilisateur (UI). Il s’agit notamment de menus par défaut et de barres d’outils, de cadres de fenêtre de documents ou de fenêtres pour enfants à interface multi-documents (MDI), de cadres de fenêtres d’outils et de support d’amarrage.

- Maintenir une liste d’exécution de tous les documents actuellement ouverts dans une table de documents en cours d’exécution (RDT) afin de coordonner la persistance des documents et de garantir qu’un document ne peut pas être ouvert de plus d’une manière, ou de manière incompatible.

- Soutenir l’interface de commande et `IOleCommandTarget`de commande-manipulation, .

- Chargement des VSPackages à des moments appropriés. Le chargement de retard d’un VSPackage est nécessaire pour améliorer les performances de la coquille.

- Gestion de certains services <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>partagés, tels que <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, qui fournit des fonctionnalités de base de la coquille, et , qui fournit des fonctionnalités de fenêtre de base.

- Gestion des fichiers solution (.sln). Les solutions contiennent des groupes de projets connexes, semblables aux fichiers d’espace de travail (.dsw) dans visual C 6.0.

- Suivi de la sélection, du contexte et de la monnaie à l’échelle de la coquille. La coque suit les types d’articles suivants :

  - Le projet actuel

  - L’élément de projet actuel ou ItemID le courant<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - La sélection actuelle pour la fenêtre **Propriétés** ou`SelectionContainer`

  - Les UDI de contexte d’interface utilisateur ou les scuids qui contrôlent la visibilité des commandes, des menus et des barres d’outils

  - Les éléments actuellement actifs tels que la fenêtre active, le document et le gestionnaire de défaire

  - Le contexte utilisateur attribue l’aide dynamique

  La coquille assure également la médiation de la communication entre les VSPackages installés et les services actuels. Il prend en charge les caractéristiques de base de la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]coquille et les met à la disposition de tous les VSPackages intégrés dans . Ces caractéristiques de base comprennent les éléments suivants :

- **À propos de** la boîte de dialogue et de l’écran d’éclaboussure

- Ajouter de nouvelles boîtes de dialogue **d’objets et ajouter des** articles existants

- **Fenêtre de vue** de classe et **navigateur d’objet**

- **Boîtes** de dialogue de références

- **Fenêtre de contour de document**

- **Fenêtre d’aide dynamique**

- **Trouver** et **remplacer**

- **Open Project** et **Open File** dialog boxes sur le **nouveau** menu

- Boîte de dialogue **d’options** sur le menu **Outils**

- **Fenêtre de propriétés**

- **Explorateur de solutions**

- **Fenêtre de la liste de** tâches

- **Boîte à outils**

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
