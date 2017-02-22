---
title: "Proc&#233;dure&#160;: exporter un nuanceur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: 11
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 11
---
# Proc&#233;dure&#160;: exporter un nuanceur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ce document montre comment utiliser le concepteur Shader pour exporter un nuanceur DGSL \(Directed Graph Shader Language\) pour pouvoir l'utiliser dans votre application.  
  
 Ce document montre cette activité :  
  
-   Exportation d'un nuanceur  
  
## Exportation d'un nuanceur  
 Après avoir créé un nuanceur à l'aide du concepteur Shader et avant de l'utiliser dans votre application, vous devez l'exporter dans un format que l'API graphique peut comprendre.  Vous pouvez exporter un nuanceur de différentes façons pour répondre aux besoins individuels.  
  
#### Pour exporter un nuanceur  
  
1.  Dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ouvrez un fichier **Graphe de nuanceur visuel \(.dgsl\)**.  
  
     Si vous n'avez pas de fichier **Graphe de nuanceur visuel \(.dgsl\)** à ouvrir, créez\-en un comme décrit dans [Comment : créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  Dans la barre d'outils **Shader Designer**, choisissez **Avancés**, **Exporter**, **Exporter en tant que**.  La boîte de dialogue **Exporter le nuanceur** s'affiche.  
  
3.  Dans la liste déroulante **Type de fichier**, choisissez le format à exporter.  
  
     Voici les formats que vous pouvez choisir :  
  
     **Nuanceur de pixels HLSL \(\*.hlsl\)**  
     Exporte le nuanceur en tant que code source HLSL \(High Level Shader Language\).  Cette option permet de modifier ultérieurement le nuanceur, même après son déploiement dans une application.  Cela peut simplifier le débogage et la correction de code en fonction des problèmes rencontrés par les utilisateurs, mais cela facilite également la modification non souhaitée de votre nuanceur par un utilisateur, par exemple pour obtenir un avantage frauduleux dans une compétition.  Elle peut aussi augmenter le temps de chargement du shader.  
  
     **Nuanceur de pixels compilé \(\*.cso\)**  
     Exporte le nuanceur en tant que bytecode HLSL.  Cette option permet de modifier ultérieurement le nuanceur, même après son déploiement dans une application.  Cela peut simplifier le débogage et la correction de code en fonction des problèmes rencontrés par les utilisateurs, mais comme le nuanceur est précompilé, il n'entraîne pas la charge d'exécution supplémentaire lorsque le nuanceur est chargé par l'application.  Les utilisateurs suffisamment qualifiés peuvent toujours modifier le nuanceur de manière non\-autorisée, mais la compilation du nuanceur rend cela plus difficile.  
  
     **En\-tête C\+\+ \(\*.h\)**  
     Exporte le nuanceur en tant qu'en\-tête de style C qui définit un tableau d'octets contenant le bytecode HLSL.  Cette option peut allonger le temps de débogage et de correction de code en fonction des problèmes rencontrés par les utilisateurs, car l'application doit être recompilée pour tester le correctif.  Toutefois, étant donné que cette option la rend plus difficile, bien que non impossible, pour modifier le nuanceur après son déploiement dans une application, elle présente le plus difficile à un utilisateur qui souhaite modifier le nuanceur de manière indésirable.  
  
4.  Dans la zone de liste déroulante **Nom de fichier**, spécifiez un nom pour le nuanceur exporté, puis choisissez le bouton **Enregistrer**.  
  
## Voir aussi  
 [Comment : créer un nuanceur de couleur de base](../designers/how-to-create-a-basic-color-shader.md)   
 [Concepteur Shader](../designers/shader-designer.md)