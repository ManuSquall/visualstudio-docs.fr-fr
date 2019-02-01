---
title: 'Procédure : Spécifiez un autre emplacement pour le déploiement des mises à jour | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ca1f9c8879130abfd762aea4b803e7734433b8d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930665"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Procédure : Spécifier un autre emplacement pour les mises à jour du déploiement
Vous pouvez installer votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application initialement à partir d’un CD ou un partage de fichiers, mais l’application doit rechercher les mises à jour périodiques sur le Web. Vous pouvez spécifier un autre emplacement pour les mises à jour dans votre manifeste de déploiement afin que votre application peut mettre à jour lui-même à partir du Web après son installation initiale.  
  
> [!NOTE]
>  Votre application doit être configurée pour installer localement pour utiliser cette fonctionnalité. Pour plus d’informations, consultez [Procédure pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). En outre, si vous installez un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à partir du réseau, définissez un autre emplacement causes [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] utilise cet emplacement pour l’installation initiale et toutes les mises à jour ultérieures. Si vous installez votre application localement (par exemple, à partir d’un CD), l’installation initiale est effectuée à l’aide du support d’origine, et toutes les mises à jour ultérieures utilisera l’autre emplacement.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Spécifiez un autre emplacement pour les mises à jour à l’aide de MageUI.exe (utilitaire Windows Forms)  
  
1.  Ouvrez une invite de commande de .NET Framework et tapez :  
  
     **mageui.exe**  
  
2.  Sur le **fichier** menu, choisissez **ouvrir** pour ouvrir le manifeste de déploiement de votre application.  
  
3.  Sélectionnez l’onglet **Options de déploiement**.  
  
4.  Dans la zone de texte nommé **Launch Location**, entrez l’URL vers le répertoire qui contient le manifeste de déploiement des mises à jour de l’application.  
  
5.  Enregistrez le manifeste de déploiement.  
  
### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Spécifiez un autre emplacement pour les mises à jour à l’aide de Mage.exe  
  
1. Ouvrez une invite de commandes du .NET Framework.  
  
2. Définissez l’emplacement de mise à jour à l’aide de la commande suivante. Dans cet exemple, *HelloWorld.exe.application* est le chemin d’accès à votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application, qui a toujours l’extension .application, et *<http://adatum.com/Update/Path>* est l’URL que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rechercheront des mises à jour de l’application.  
  
    **Mage-mettre à jour HelloWorld.exe.application - ProviderUrl http://adatum.com/Update/Path**  
  
3. Enregistrez le fichier.  
  
   > [!NOTE]
   >  Vous devez maintenant signer à nouveau le fichier avec *Mage.exe*. Pour plus d’informations, consultez [Procédure pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Si vous installez votre application à partir d’un support hors connexion tel qu’un CD, et l’ordinateur est en ligne, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vérifie d’abord l’URL spécifiée par la `<deploymentProvider>` balise dans le manifeste de déploiement pour déterminer si l’emplacement de mise à jour contient une version plus récente de la application. Le cas échéant, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installe l’application directement à partir de là, au lieu d’à partir du répertoire d’installation initiale, et le common language runtime (CLR) détermine le niveau de confiance de votre application à l’aide de niveau `<deploymentProvider>`. Si l’ordinateur est hors connexion, ou `<deploymentProvider>` est inaccessible, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installe à partir du CD et le CLR accorde la confiance que basée sur le point d’installation ; pour une installation CD, cela signifie que votre application reçoit une confiance totale. Toutes les mises à jour ultérieures hériteront de ce niveau de confiance.  
  
 Tous les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] les applications qui utilisent `<deploymentProvider>` doit déclarer explicitement les autorisations dont ils ont besoin dans leur manifeste d’application, afin que l’application ne reçoit pas de différents niveaux de confiance sur différents ordinateurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)