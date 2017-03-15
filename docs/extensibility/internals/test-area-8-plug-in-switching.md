---
title: "Test zone 8: Commutation plug-in | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "contrôle de code source (Visual Studio SDK), basculement de plug-ins"
  - "contrôle plug-ins de source, changement"
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Test zone 8: Commutation plug-in
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a l' \(UI\)interface utilisateur pour modifier le plug\-in actuel de contrôle de code source.  Cette zone de test fournit des cas de test pour le processus de la cueillette qui plug\-in à utiliser pour le contrôle de code source de la solution.  
  
## menu Access de commande  
 Les chemins d'accès suivants de menu d'environnement de développement intégré \(IDE\) de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sont utilisés dans des scénarios de test.  
  
-   plug\-in actuel de contrôle de code source : **Outils** \- \> **Options** \- \> **Contrôle de source de données** \- \> **Sélection de plug\-in**.  
  
-   Liaison du contrôle de code source de modification : **Fichier** \- \> **Contrôle de source de données** \- \> **Contrôle de modifier le code source**…  
  
## Comportement attendu par commun  
 Modifier le plug\-in contrôle de code source d'une solution est possible sans quitter Visual Studio ou recharger la solution.  En outre, le plug\-in actuel de contrôle de code source change automatiquement à celui utilisé par une solution lorsque cette solution est chargée.  
  
## Cas de test  
 Voici des scénarios de test spécifiques pour la zone de test basculante de plug\-in.  
  
### cas 8a : modification automatique  
  
#### Comportement attendu  
 Lorsqu'un utilisateur charge une solution sous contrôle de code source, la solution est automatiquement chargée et le plug\-in approprié de contrôle de code source est sélectionné comme actif.  
  
|Action|étapes de test|résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Modification du plug\-in du contrôle de code source automatique|1.  Sélectionnez le plug\-in testée comme actif \(**Outils** \- \> **Options** \- \> **Contrôle de source de données** \- \> **Sélection de plug\-in**.\)<br />2.  Création d'un nouveau projet.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  sélectionnez un autre plug\-in \(par exemple, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />5.  Accept déchargement l'invite de solution.<br />6.  Rouvrez la solution à partir de le disque.|la solution est ouverte.<br /><br /> Le plug\-in testée est le plug\-in actuel de contrôle de code source.|  
  
### cas 8b : modification Solution\-basée  
  
#### Comportement attendu  
 la solution peut avoir son plug\-in associé de contrôle de code source modifié.  
  
|Action|étapes de test|résultats attendus à vérifier|  
|------------|--------------------|-----------------------------------|  
|Modification de plug\-in d'une solution|1.  Sélectionnez le plug\-in testée comme actif \(**Outils** \- \> **Options** \- \> **Contrôle de source de données** \- \> **Sélection de plug\-in**\).<br />2.  Créez un nouveau projet et solution.<br />3.  Ajouter la solution au contrôle de code source.<br />4.  Supprimez la liaison de la solution du contrôle de code source \(en utilisant la boîte de dialogue **Contrôle de modifier le code source** \).<br />5.  sélectionnez un autre plug\-in \(par exemple, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />6.  Rechargez la solution à partir de le disque si déchargé.<br />7.  Ajouter la solution au contrôle de code source.<br />8.  Supprimez la liaison de la solution du contrôle de code source \(en utilisant la boîte de dialogue **Contrôle de modifier le code source** \).<br />9. Sélectionnez le plug\-in au test.<br />10. Solution de rechargement à partir de le disque si déchargé.<br />11. Liez la solution dans l'emplacement d'origine \(en utilisant la boîte de dialogue **Contrôle de modifier le code source** \).|La solution est ajoutée au contrôle de code source à l'aide de le plug\-in sélectionné.|  
  
## Voir aussi  
 [Guide d'évaluation pour les Plug\-ins de contrôle de code Source](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)