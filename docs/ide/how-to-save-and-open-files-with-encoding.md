---
title: "Comment&#160;: enregistrer et ouvrir des fichiers avec encodage | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "prise en charge des langues bidirectionnelles, fichiers encodés"
  - "encodage de fichier, langues bidirectionnelles"
  - "fichiers, encoding"
  - "Unicode, prise en charge des langues bidirectionnelles"
ms.assetid: cb52b732-b395-4ba1-a3ef-104b3942a12a
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comment&#160;: enregistrer et ouvrir des fichiers avec encodage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez enregistrer des fichiers avec un encodage de caractères spécifique permettant la prise en charge des langues bidirectionnelles.  Vous pouvez également spécifier un encodage à l'ouverture d'un fichier de sorte que Visual Studio l'affiche correctement.  
  
### Pour enregistrer un fichier avec un encodage  
  
1.  Dans le menu **Fichier**, choisissez **Enregistrer le fichier sous**, puis cliquez sur le bouton déroulant à côté du bouton **Enregistrer**.  
  
     La boîte de dialogue **Options d'enregistrement avancées** s'affiche.  
  
2.  Sous **Encodage**, sélectionnez le codage à utiliser pour le fichier.  
  
3.  Sous **Fins de ligne**, vous pouvez éventuellement sélectionner le format pour les caractères de fin de ligne.  
  
     Cette option est utile lorsque vous souhaitez échanger le fichier avec des utilisateurs disposant d'un système d'exploitation différent.  
  
     Si vous souhaitez utiliser un fichier dont vous savez qu'il est encodé de manière spécifique, vous pouvez indiquer à Visual Studio d'utiliser ce codage à l'ouverture du fichier.  La méthode d'ouverture du fichier dépend de son appartenance \(membership\) ou non à votre projet.  
  
### Pour ouvrir un fichier encodé faisant partie d'un projet  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier, puis choisissez **Ouvrir avec**.  
  
2.  Dans la boîte de dialogue **Ouvrir avec**, choisissez l'éditeur avec lequel ouvrir le fichier.  
  
     De nombreux éditeurs Visual Studio, tels que l'éditeur de formulaires, détectent automatiquement l'encodage et ouvrent le fichier de façon appropriée.  Si vous choisissez un éditeur qui vous permet de choisir le codage, la boîte de dialogue **Encodage** s'affiche.  
  
3.  Dans la boîte de dialogue **Encodage**, sélectionnez le codage à utiliser par l'éditeur.  
  
### Pour ouvrir un fichier encodé ne faisant pas partie d'un projet  
  
1.  Dans le menu **Fichier**, pointez sur **Ouvrir**, choisissez **Fichier** ou **Fichier à partir du Web**, puis sélectionnez le fichier à ouvrir.  
  
2.  Cliquez sur le bouton déroulant à côté du bouton **Ouvrir**, puis choisissez **Ouvrir avec**.  
  
3.  Répétez les étapes 2 et 3 de la procédure précédente.  
  
## Voir aussi  
 [Encodage et globalisation des applications Windows Forms](../Topic/Encoding%20and%20Windows%20Forms%20Globalization.md)   
 [Globalisation et localisation d'applications](../ide/globalizing-and-localizing-applications.md)