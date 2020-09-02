---
title: 'Comment : déboguer une application de confiance partielle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 030fef750cc1e0f0932de32fca1a0ffef56bc8f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704483"
---
# <a name="how-to-debug-a-partial-trust-application"></a>Comment : déboguer une application de confiance partielle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S'applique aux applications Windows et console.  
  
 La [sécurité et le déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md) facilitent le déploiement d’applications de confiance partielle qui tirent parti de la [sécurité d’accès du code](https://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) pour limiter l’accès aux ressources sur un ordinateur.  
  
 Le débogage d'une application de confiance partielle peut être un défi, parce que les applications de confiance partielle ont des autorisations de sécurité différentes (et par conséquent se comportent différemment) selon l'emplacement à partir duquel elles sont installées. Une application de confiance partielle installée à partir d'internet dispose d'un nombre limité d'autorisations. Si elle est installée depuis un intranet local, elle dispose d'un plus grand nombre d'autorisations ; si elle est installée à partir de l'ordinateur local, elle bénéficie des autorisations maximales. Vous pouvez également définir des zones personnalisées associées à des autorisations personnalisées. Vous pouvez devoir déboguer une application de confiance partielle dans l'une ou l'ensemble des conditions suivantes. Heureusement, Visual Studio vous facilite également la tâche.  
  
 Avant de démarrer une session de débogage dans Visual Studio, vous pouvez choisir la zone à partir de laquelle vous voulez simuler l'installation d'une application. Lorsque vous commencez à déboguer, l'application dispose des autorisations appropriées pour une application de confiance partielle installée à partir de cette zone. Cela vous permet d'examiner le comportement de l'application comme il apparaîtrait à un utilisateur qui l'aurait téléchargée à partir de cette zone.  
  
 Si l'application tente d'exécuter une action pour laquelle elle n'a pas d'autorisation, une exception se produit. À ce stade, l'Assistant Exception vous donne une occasion d'ajouter une autorisation supplémentaire, qui vous permet de redémarrer la session de débogage avec les autorisations suffisantes pour éviter le problème.  
  
 Ultérieurement, vous pourrez revenir en arrière et consulter les autorisations que vous avez ajoutées pendant le débogage. Le fait de devoir ajouter une autorisation lors du débogage indique probablement la nécessité d'ajouter une invite d'autorisation de l'utilisateur à cet endroit du code.  
  
> [!NOTE]
> Les visualiseurs de débogueur requièrent des privilèges plus importants que ceux octroyés par une application de confiance partielle. Les visualiseurs ne se chargent pas lorsque vous êtes arrêté dans du code à confiance partielle. Pour déboguer à l'aide d'un visualiseur, vous devez exécuter le code avec la confiance totale.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Pour choisir une zone pour votre application de confiance partielle  
  
1. Dans le menu **projet** , choisissez _Projectname_**Propriétés**ProjectName.  
  
2. Dans les pages de propriétés *ProjectName* , cliquez sur la page **sécurité** .  
  
3. Sélectionnez **activer les paramètres de sécurité ClickOnce**.  
  
4. Sous **zone à partir de laquelle votre application sera installée**, cliquez sur la zone de liste déroulante et choisissez la zone à partir de laquelle vous voulez simuler l’installation.  
  
     Les **autorisations requises par la grille application** affichent toutes les autorisations disponibles. La coche indique les autorisations accordées à votre application.  
  
5. Si la zone que vous choisissez était **(personnalisée)**, sélectionnez les paramètres personnalisés corrects dans la colonne **paramètre** de la grille **autorisations** .  
  
6. Cliquez sur **OK** pour fermer les pages de propriétés.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Pour ajouter une autorisation supplémentaire lorsqu'une exception de sécurité se produit  
  
1. La boîte de dialogue **Assistant Exception** s’affiche avec le message : **SecurityException n’a pas été gérée.**  
  
2. Dans la boîte de dialogue **Assistant Exception** , sous **actions**, cliquez sur **Ajouter une autorisation au projet**.  
  
3. La boîte de dialogue **redémarrer le débogage** s’affiche.  
  
    - Si vous souhaitez redémarrer la session de débogage avec la nouvelle autorisation, cliquez sur **Oui**.  
  
    - Si vous ne souhaitez pas encore redémarrer, cliquez sur **non**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Pour afficher les autorisations supplémentaires ajoutées pendant le débogage  
  
1. Dans le menu **projet** , choisissez _Projectname_**Propriétés**ProjectName.  
  
2. Dans les pages de propriétés *ProjectName* , cliquez sur la page **sécurité** .  
  
3. Examinez les **autorisations requises par la grille de l’application** . Toutes les autorisations supplémentaires que vous avez ajoutées ont deux icônes dans la colonne **inclus** : la coche normale, qui comprend toutes les autorisations incluses, et une icône supplémentaire, qui ressemble à une info-bulle contenant la lettre « i ».  
  
4. Utilisez la barre de défilement verticale pour afficher l’ensemble des **autorisations requises par la grille de l’application** .  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité et déploiement ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)
