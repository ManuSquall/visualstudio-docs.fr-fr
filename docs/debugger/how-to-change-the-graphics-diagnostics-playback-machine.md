---
title: "Comment&#160;: modifier l&#39;ordinateur de lecture Graphics Diagnostics | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: modifier l&#39;ordinateur de lecture Graphics Diagnostics
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez lire les informations graphiques en utilisant votre ordinateur local, ou en utilisant un ordinateur ou un périphérique distant.  
  
## Choix d'un ordinateur de lecture  
 L'ordinateur de lecture est un ordinateur ou un périphérique utilisé pour lire des événements graphiques à partir d'un journal graphique.  En général, l'ordinateur local est l'option la plus pratique, mais un problème de rendu ne peut pas se reproduire sur un ordinateur équipé de versions de matériel ou de pilote différentes de l'ordinateur sur lequel il a été capturé. Lorsque cela se produit, vous pouvez choisir un ordinateur de lecture à distance qui reproduit mieux le problème tout en continuant à utiliser votre ordinateur de développement pour le diagnostiquer.  
  
#### Pour utiliser l'ordinateur local pour lire les informations graphiques  
  
1.  Dans la fenêtre de document du journal Graphics, choisissez le lien **Ordinateur de lecture**.  La boîte de dialogue **Connexions au débogueur distant** s'affiche.  
  
2.  Sous **Configuration manuelle**, dans la propriété **Adresse**, entrez `localhost`.  
  
3.  Définissez la propriété **Mode d'authentification** sur la valeur **Aucun**.  
  
4.  Choisissez le bouton **Sélectionner**.  
  
#### Pour utiliser un ordinateur distant pour lire les informations graphiques  
  
1.  Dans la fenêtre de document du journal Graphics, choisissez le lien **Ordinateur de lecture**.  La boîte de dialogue **Connexions au débogueur distant** s'affiche.  
  
2.  Sous **Configuration manuelle**, dans la propriété **Adresse**, entrez le nom de domaine Windows ou l'adresse IP de l'ordinateur ou du périphérique que vous souhaitez utiliser pour lire les informations graphiques.  
  
3.  Spécifiez le type d'autorisation que vous souhaitez utiliser pour sécuriser la connexion à l'ordinateur de lecture.  
  
    -   Pour l'authentification Windows, définissez la propriété **Mode d'authentification** sur la valeur **Windows**.  
  
    -   Pour aucune authentification, définissez la propriété **Mode d'authentification** sur la valeur **Aucune**.  
  
4.  Choisissez le bouton **Sélectionner**.  
  
> [!NOTE]
>  La boîte de dialogue **Connexions au débogueur distant** peut également afficher les cibles de débogage distant qui sont directement connectées à votre ordinateur de développement ou qui se trouvent sur le même sous\-réseau.  Vous pouvez utiliser l'une de ces cibles de débogage distant comme ordinateur de lecture Graphics Diagnostics sans la configurer manuellement.  Dans la boîte de dialogue **Connexions au débogueur distant**, sélectionnez la cible que vous souhaitez, puis choisissez le bouton **Sélectionner**.  
  
## Voir aussi  
 [Document de journal Graphics](../debugger/graphics-log-document.md)