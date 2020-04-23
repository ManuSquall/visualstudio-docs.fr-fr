---
title: 'Comment : Spécifier un autre emplacement pour les mises à jour du déploiement ( Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- deployment update, alternative locations
ms.assetid: 7faacd35-2638-492d-80f6-6b57e5f820de
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b6388833e6574fc1d631d391fa7b67d5f0a3372
ms.sourcegitcommit: c1339f64fbeee6f17bf80fedea81afc8dac40dc0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82037218"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Comment : spécifier un autre emplacement pour les mises à jour du déploiement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installer votre application au départ à partir d’un CD ou d’une part de fichier, mais l’application doit vérifier les mises à jour périodiques sur le Web. Vous pouvez spécifier un autre emplacement pour les mises à jour dans votre manifeste de déploiement afin que votre application puisse se mettre à jour à partir du Web après son installation initiale.  
  
> [!NOTE]
> Votre application doit être configurée pour installer localement pour utiliser cette fonctionnalité. Pour plus d’informations, voir [Procédure Pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). En outre, si [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vous installez une application à [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] partir du réseau, le réglage d’un autre emplacement provoque d’utiliser cet emplacement à la fois pour l’installation initiale et toutes les mises à jour ultérieures. Si vous installez votre application localement (par exemple, à partir d’un CD), l’installation initiale est effectuée à l’aide du support d’origine, et toutes les mises à jour ultérieures utiliseront l’emplacement alternatif.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Spécifier un autre emplacement pour les mises à jour en utilisant MageUI.exe (Windows Forms-based utility)  
  
1. Ouvrez une invite et un type de commande cadre .NET :  
  
     **mageui.exe**  
  
2. Sur le menu **Fichier,** choisissez **Open** pour ouvrir le manifeste de déploiement de votre application.  
  
3. Sélectionnez l’onglet **Options de déploiement**.  
  
4. Dans la boîte de texte nommée **Lieu de lancement**, entrez l’URL à l’annuaire qui contiendra le manifeste de déploiement pour les mises à jour de l’application.  
  
5. Enregistrer le manifeste de déploiement.  
  
### <a name="specifying-an-alternate-location-for-updates-by-using-mageexe"></a>Spécifier un autre emplacement pour les mises à jour en utilisant Mage.exe  
  
1. Ouvrez une invite de commandes du .NET Framework.  
  
2. Définissez l’emplacement de mise à jour à l’aide de la commande suivante. Dans cet exemple, **HelloWorld.exe.application** est [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] le chemin vers votre manifeste d’application, qui a toujours l’extension .application, et `http://adatum.com/Update/Path` est l’URL qui [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vérifiera les mises à jour de l’application.  
  
     **Mage -Mise à jour HelloWorld.exe.application\/-ProviderUrl http: /adatum.com/Update/Path**  
  
3. Enregistrez le fichier .  
  
    > [!NOTE]
    > Vous devez maintenant re-signer le fichier avec Mage.exe. Pour plus d’informations, voir [Procédure Pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Si vous installez votre application à partir d’un support [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] hors connexion tel qu’un CD, et que l’ordinateur est en ligne, vérifie d’abord l’URL spécifiée par l’étiquette `<deploymentProvider>` dans le manifeste de déploiement pour déterminer si l’emplacement de mise à jour contient une version plus récente de l’application. Si c’est le cas, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] installe l’application directement à partir de là, au lieu de l’annuaire d’installation initial, et l’heure courante de l’exécution de la langue (CLR) détermine le niveau de confiance de votre application en utilisant `<deploymentProvider>`. Si l’ordinateur est `<deploymentProvider>` hors ligne, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ou est inaccessible, installe à partir du CD, et le CLR accorde la confiance en fonction du point d’installation; pour une installation de CD, cela signifie que votre application reçoit la pleine confiance. Toutes les mises à jour ultérieures hériteront de ce niveau de confiance.  
  
 Toutes [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] les `<deploymentProvider>` applications qui utilisent doivent déclarer explicitement les autorisations dont elles ont besoin dans leur manifeste d’application, de sorte que l’application ne reçoit pas différents niveaux de confiance sur différents ordinateurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)   
 [Sécurisation des applications ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Choix d’une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
