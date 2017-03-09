---
title: "Comment&#160;: d&#233;boguer une application de confiance partielle | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "déboguer (Visual Studio), applications de confiance partielle"
  - "applications de confiance partielle"
  - "sécurité (Visual Studio), applications de confiance partielle"
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: d&#233;boguer une application de confiance partielle
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

S'applique aux applications Windows et console.  
  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md) facilite le déploiement d'applications de confiance partielle qui tirent parti de [Sécurité d'accès du code](../Topic/Code%20Access%20Security.md) pour limiter l'accès aux ressources sur un ordinateur.  
  
 Le débogage d'une application de confiance partielle peut être un défi, parce que les applications de confiance partielle ont des autorisations de sécurité différentes \(et par conséquent se comportent différemment\) selon l'emplacement à partir duquel elles sont installées.  Une application de confiance partielle installée à partir d'internet dispose d'un nombre limité d'autorisations.  Si elle est installée depuis un intranet local, elle dispose d'un plus grand nombre d'autorisations ; si elle est installée à partir de l'ordinateur local, elle bénéficie des autorisations maximales.  Vous pouvez également définir des zones personnalisées associées à des autorisations personnalisées.  Vous pouvez devoir déboguer une application de confiance partielle dans l'une ou l'ensemble des conditions suivantes.  Heureusement, Visual Studio vous facilite également la tâche.  
  
 Avant de démarrer une session de débogage dans Visual Studio, vous pouvez choisir la zone à partir de laquelle vous voulez simuler l'installation d'une application.  Lorsque vous commencez à déboguer, l'application dispose des autorisations appropriées pour une application de confiance partielle installée à partir de cette zone.  Cela vous permet d'examiner le comportement de l'application comme il apparaîtrait à un utilisateur qui l'aurait téléchargée à partir de cette zone.  
  
 Si l'application tente d'exécuter une action pour laquelle elle n'a pas d'autorisation, une exception se produit.  À ce stade, l'Assistant Exception vous donne une occasion d'ajouter une autorisation supplémentaire, qui vous permet de redémarrer la session de débogage avec les autorisations suffisantes pour éviter le problème.  
  
 Ultérieurement, vous pourrez revenir en arrière et consulter les autorisations que vous avez ajoutées pendant le débogage.  Le fait de devoir ajouter une autorisation lors du débogage indique probablement la nécessité d'ajouter une invite d'autorisation de l'utilisateur à cet endroit du code.  
  
> [!NOTE]
>  Les visualiseurs de débogueur requièrent des privilèges plus importants que ceux octroyés par une application de confiance partielle.  Les visualiseurs ne se chargent pas lorsque vous êtes arrêté dans du code à confiance partielle.  Pour déboguer à l'aide d'un visualiseur, vous devez exécuter le code avec la confiance totale.  
  
### Pour choisir une zone pour votre application de confiance partielle  
  
1.  Dans le menu **Projet**, choisissez Propriétés de *Projectname*.  
  
2.  Dans les pages de propriétés de *Projectname*, cliquez sur la page **Sécurité**.  
  
3.  Sélectionnez **Activer les paramètres de sécurité ClickOnce**.  
  
4.  Sous **Zone à partir de laquelle votre application sera installée**, cliquez sur la zone de liste déroulante et choisissez la zone à utiliser comme emplacement à partir duquel l'application sera installée.  
  
     La grille **Autorisations requises par l'application** affiche toutes les autorisations disponibles.  La coche indique les autorisations accordées à votre application.  
  
5.  Si vous choisissez la zone **\(Personnalisée\)**, sélectionnez les paramètres personnalisés corrects dans la colonne **Paramètre** de la grille **Autorisations**.  
  
6.  Cliquez sur **OK** pour fermer les pages de propriétés.  
  
### Pour ajouter une autorisation supplémentaire lorsqu'une exception de sécurité se produit  
  
1.  La boîte de dialogue **Assistant Exception** s'affiche avec le message : SecurityException n'a pas été gérée.  
  
2.  Dans la boîte de dialogue **Assistant Exception**, sous **Actions**, cliquez sur **Ajouter une autorisation au projet**.  
  
3.  La boîte de dialogue **Redémarrer le débogage** s'affiche.  
  
    -   Si vous souhaitez redémarrer la session de débogage avec la nouvelle autorisation, cliquez sur **Oui**.  
  
    -   Si vous ne souhaitez pas redémarrer à ce stade, cliquez sur **Non**.  
  
### Pour afficher les autorisations supplémentaires ajoutées pendant le débogage  
  
1.  Dans le menu **Projet**, choisissez Propriétés de *Projectname*.  
  
2.  Dans les pages de propriétés de *Projectname*, cliquez sur la page **Sécurité**.  
  
3.  Examinez la grille **Autorisations requises par l'application**.  Toute autorisation supplémentaire que vous avez ajoutée a deux icônes dans la colonne **Inclus** : la coche normale associée à toutes les autorisations incluses ainsi qu'une icône supplémentaire qui ressemble à un ballon contenant la lettre "i".  
  
4.  Utilisez la barre de défilement verticale pour consulter l'intégralité de la grille **Autorisations requises par l'application**.  
  
## Voir aussi  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)