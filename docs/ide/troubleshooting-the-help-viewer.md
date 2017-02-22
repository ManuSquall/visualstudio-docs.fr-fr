---
title: "R&#233;solution des probl&#232;mes li&#233;s &#224; la Visionneuse d&#39;aide | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Help Viewer 2.0, dépanner"
  - "résolution des problèmes (Help Viewer 2.0)"
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# R&#233;solution des probl&#232;mes li&#233;s &#224; la Visionneuse d&#39;aide
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique traite des problèmes que vous pouvez rencontrer avec la visionneuse d'aide \(Help Viewer\).  
  
## L'audio ne fonctionne pas.  
 La visionneuse d'aide \(Help Viewer\) ne comporte pas de lecteur audio.  Si vous téléchargez un contenu avec de l'audio et que rie ne se passe quand **Lecture** est sélectionné, installez un lecteur audio.  
  
## Le recherche ne fonctionne pas dans Windows Server 2008, Windows Server 2008 avec SP1 ou Windows Server 2008 R2.  
 Les fonctionnalités de recherche et de filtrage de la visionneuse d'aide \(Help Viewer\) requièrent que le service de recherche Windows soit installé et activé.  Par défaut, ce service est désactivé dans Windows Server 2008, Windows Server 2008 avec Service Pack 1 \(SP1\) et Windows Server 2008 R2.  
  
#### Pour activer le service de recherche Windows  
  
1.  Démarrez le Gestionnaire de serveur.  
  
2.  Dans le volet de navigation gauche, sélectionnez **Rôles**.  
  
3.  Dans le volet Résumé des rôles, choisissez **Ajouter le rôle**.  
  
4.  Sélectionnez le rôle Services de fichiers, puis sélectionnez le bouton **Suivant**.  
  
5.  Sélectionnez le service de rôle de recherche Windows.  
  
## Ressources supplémentaires  
 Obtenez plus d'informations et fournissez des commentaires sur la visionneuse d'aide à l'aide des ressources suivantes :  
  
-   Pour fournir des commentaires, consultez [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) sur le site Web Microsoft ou envoyez un courrier électronique à [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
-   Pour plus d'informations, consultez le forum [Developer Documentation and Help System \(Documentation et système d'aide du développeur\)](http://go.microsoft.com/fwlink/?LinkId=232741) et le blog [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743).  
  
## Voir aussi  
 [Guide de l'administrateur de la Visionneuse d'aide 2.1](http://go.microsoft.com/fwlink/?LinkId=243985)