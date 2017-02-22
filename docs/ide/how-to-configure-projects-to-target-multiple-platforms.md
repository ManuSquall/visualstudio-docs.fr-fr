---
title: "Comment&#160;: configurer des projets pour plusieurs plateformes cibles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plateformes, modifier les plateformes cibles"
  - "projets (Visual Studio), cibler des plateformes"
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Comment&#160;: configurer des projets pour plusieurs plateformes cibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permet à une solution cible plusieurs architectures d'UC, ou plateformes, à la fois.  Les propriétés pour les définir sont accessibles via la boîte de dialogue de **Gestionnaire de configurations** .  
  
## Viser une plateforme  
 La boîte de dialogue **Gestionnaire de configurations** vous permet de créer et de définir des configurations et des plateformes de niveau solution et de niveau projet.  Chaque combinaison de configurations au niveau de la solution et cibles peut avoir un jeu unique de propriétés qui lui est associé et vous permet de basculer facilement entre, par exemple, une configuration Release qui cible une plateforme [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], une configuration Release qui cible une plateforme x86, et une configuration de débogage qui cible une plateforme x86.  
  
#### Pour définir votre configuration en fonction d'une plateforme différente  
  
1.  Dans le menu **Générer**, choisissez **Gestionnaire de configurations**  
  
2.  Dans la zone **plateforme de la solution active**, sélectionnez la plateforme que vous souhaitez que votre solution vise, ou sélectionnez **\<Nouveau\>** pour créer une nouvelle plateforme.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compile votre application pour cibler la plateforme définie comme plateforme active dans la boîte de dialogue de **Gestionnaire de configurations** .  
  
## Suppression d'une plateforme  
 Si vous réalisez que vous n'avez aucun besoin d'une plateforme, vous pouvez la supprimer à l'aide de la boîte de dialogue Gestionnaire de configurations.  Cela supprimera tous les paramètres de solution et de projet que vous avez configurés pour cette combinaison de configuration et de cible.  
  
#### Pour supprimer une plateforme  
  
1.  Dans le menu **Générer**, choisissez **Gestionnaire de configurations**  
  
2.  Dans la zone **plateforme de la solution active**, sélectionnez **\<Modifier\>**.  La boîte de dialogue **Modifier les plateformes de solution** s'affiche.  
  
3.  Cliquez sur la plateforme à supprimer, puis cliquez sur **Supprimer**.  
  
## Viser plusieurs plateformes avec une solution  
 Étant donné que vous pouvez changer les paramètres basés sur la combinaison des paramètres de configuration et de plateforme, vous pouvez configurer une solution capable de viser plusieurs plateformes.  
  
#### Pour viser plusieurs plateformes  
  
1.  Utilisez le **Gestionnaire de configurations** pour ajouter au moins deux plateformes cibles pour la solution.  
  
2.  Sélectionnez la plateforme que vous voulez viser dans la liste **plateforme de la solution active**.  
  
3.  Générez la solution.  
  
#### Pour générer plusieurs configurations de solution à la fois  
  
1.  Utilisez le **Gestionnaire de configurations** pour ajouter au moins deux plateformes cibles pour la solution.  
  
2.  Utilisez la fenêtre **Générer en tâche de fond** pour générer plusieurs configurations de solution à la fois.  
  
 Il est possible d'avoir une plateforme au niveau de la solution, par exemple, [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], sans projets dans cette solution qui cible la même plateforme.  Il est également possible d'avoir plusieurs projets dans votre solution, chacun visant une plateforme différente.  Si telle est votre situation, il est recommandé de créer une nouvelle configuration portant un nom descriptif, afin d'éviter toute confusion.  
  
## Voir aussi  
 [Comment : créer et modifier des configurations](../ide/how-to-create-and-edit-configurations.md)   
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)