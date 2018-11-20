---
title: 'Comment : déboguer une Application de confiance partielle | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76cce8cfcf57f956b5de16b72f7a275e1d629630
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782048"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Comment : déboguer une application de confiance partielle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S'applique aux applications Windows et console.  
  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md) rend plus facile de déployer des applications de confiance partielle qui tirent parti de [Code Access Security](http://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) pour limiter l’accès aux ressources sur un ordinateur.  
  
 Le débogage d'une application de confiance partielle peut être un défi, parce que les applications de confiance partielle ont des autorisations de sécurité différentes (et par conséquent se comportent différemment) selon l'emplacement à partir duquel elles sont installées. Une application de confiance partielle installée à partir d'internet dispose d'un nombre limité d'autorisations. Si elle est installée depuis un intranet local, elle dispose d'un plus grand nombre d'autorisations ; si elle est installée à partir de l'ordinateur local, elle bénéficie des autorisations maximales. Vous pouvez également définir des zones personnalisées associées à des autorisations personnalisées. Vous pouvez devoir déboguer une application de confiance partielle dans l'une ou l'ensemble des conditions suivantes. Heureusement, Visual Studio vous facilite également la tâche.  
  
 Avant de démarrer une session de débogage dans Visual Studio, vous pouvez choisir la zone à partir de laquelle vous voulez simuler l'installation d'une application. Lorsque vous commencez à déboguer, l'application dispose des autorisations appropriées pour une application de confiance partielle installée à partir de cette zone. Cela vous permet d'examiner le comportement de l'application comme il apparaîtrait à un utilisateur qui l'aurait téléchargée à partir de cette zone.  
  
 Si l'application tente d'exécuter une action pour laquelle elle n'a pas d'autorisation, une exception se produit. À ce stade, l'Assistant Exception vous donne une occasion d'ajouter une autorisation supplémentaire, qui vous permet de redémarrer la session de débogage avec les autorisations suffisantes pour éviter le problème.  
  
 Ultérieurement, vous pourrez revenir en arrière et consulter les autorisations que vous avez ajoutées pendant le débogage. Le fait de devoir ajouter une autorisation lors du débogage indique probablement la nécessité d'ajouter une invite d'autorisation de l'utilisateur à cet endroit du code.  
  
> [!NOTE]
>  Les visualiseurs de débogueur requièrent des privilèges plus importants que ceux octroyés par une application de confiance partielle. Les visualiseurs ne se chargent pas lorsque vous êtes arrêté dans du code à confiance partielle. Pour déboguer à l'aide d'un visualiseur, vous devez exécuter le code avec la confiance totale.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Pour choisir une zone pour votre application de confiance partielle  
  
1.  À partir de la **projet** menu, choisissez _nom_projet_**propriétés**.  
  
2.  Dans le *nom_projet* pages de propriétés, cliquez sur le **sécurité** page.  
  
3.  Sélectionnez **activer les paramètres de sécurité ClickOnce**.  
  
4.  Sous **Zone votre application sera installée à partir de**, cliquez sur la zone de liste déroulante et choisissez la zone que vous souhaitez simuler l’application en cours d’installation à partir de.  
  
     Le **autorisations requises par l’application** grille affiche toutes les autorisations disponibles. La coche indique les autorisations accordées à votre application.  
  
5.  Si vous choisissez la zone **(personnalisé)**, sélectionnez les paramètres personnalisés corrects dans le **paramètre** colonne de la **autorisations** grille.  
  
6.  Cliquez sur **OK** pour fermer les pages de propriétés.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Pour ajouter une autorisation supplémentaire lorsqu'une exception de sécurité se produit  
  
1.  Le **Assistant Exception** boîte de dialogue s’affiche avec le message : **SecurityException n’était pas gérée.**  
  
2.  Dans le **Assistant Exception** boîte de dialogue **Actions**, cliquez sur **ajouter une autorisation au projet**.  
  
3.  Le **redémarrer le débogage** boîte de dialogue s’affiche.  
  
    -   Si vous souhaitez redémarrer la session de débogage avec la nouvelle autorisation, cliquez sur **Oui**.  
  
    -   Si vous ne souhaitez pas redémarrer à ce stade, cliquez sur **non**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Pour afficher les autorisations supplémentaires ajoutées pendant le débogage  
  
1.  À partir de la **projet** menu, choisissez _nom_projet_**propriétés**.  
  
2.  Dans le *nom_projet* pages de propriétés, cliquez sur le **sécurité** page.  
  
3.  Examinez le **autorisations requises par l’application** grille. Toute autorisation supplémentaire que vous avez ajouté a deux icônes le **inclus** colonne : la coche normale associée ayant inclus toutes les autorisations et une icône supplémentaire qui ressemble à un ballon contenant la lettre « i ».  
  
4.  Utilisez la barre de défilement verticale pour consulter l’intégralité **autorisations requises par l’application** grille.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)



