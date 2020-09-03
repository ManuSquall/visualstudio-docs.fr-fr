---
title: Comment spécifier un autre emplacement pour les mises à jour de déploiement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: c71586c43fa1a71205d61ae21fb94c267daf497d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85381910"
---
# <a name="how-to-specify-an-alternate-location-for-deployment-updates"></a>Guide pratique pour spécifier un autre emplacement pour les mises à jour du déploiement
Vous pouvez installer votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application initialement à partir d’un CD ou d’un partage de fichiers, mais l’application doit rechercher les mises à jour périodiques sur le Web. Vous pouvez spécifier un autre emplacement pour les mises à jour dans votre manifeste de déploiement afin que votre application puisse se mettre à jour à partir du Web après son installation initiale.

> [!NOTE]
> Votre application doit être configurée pour s’installer localement afin d’utiliser cette fonctionnalité. Pour plus d’informations, consultez [procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). En outre, si vous installez une [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application à partir du réseau, la définition d’un autre emplacement entraîne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] l’utilisation de cet emplacement pour l’installation initiale et pour toutes les mises à jour ultérieures. Si vous installez votre application localement (par exemple, à partir d’un CD-ROM), l’installation initiale est effectuée à l’aide du support d’origine et toutes les mises à jour ultérieures utilisent l’autre emplacement.

### <a name="specify-an-alternate-location-for-updates-by-using-mageuiexe-windows-forms-based-utility"></a>Spécifier un autre emplacement pour les mises à jour à l’aide d' MageUI.exe (utilitaire basé sur Windows Forms)

1. Ouvrez une invite de commandes .NET Framework et tapez :

     **mageui.exe**

2. Dans le menu **fichier** , choisissez **ouvrir** pour ouvrir le manifeste de déploiement de votre application.

3. Sélectionnez l’onglet **Options de déploiement**.

4. Dans la zone de texte nommée **emplacement de lancement**, entrez l’URL du répertoire qui contiendra le manifeste de déploiement pour les mises à jour d’application.

5. Enregistrez le manifeste de déploiement.

### <a name="specify-an-alternate-location-for-updates-by-using-mageexe"></a>Spécifiez un autre emplacement pour les mises à jour à l’aide de Mage.exe

1. Ouvrez une invite de commandes du .NET Framework.

2. Définissez l’emplacement de la mise à jour à l’aide de la commande suivante. Dans cet exemple, *HelloWorld.exe. application* est le chemin d’accès à votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifeste d’application, qui a toujours l’extension. application et `http://adatum.com/Update/Path` est l’URL qui [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] recherche les mises à jour d’application.

    **Mage-Update HelloWorld.exe. application-ProviderUrl http : \/ /adatum.com/Update/Path**

3. Enregistrez le fichier .

   > [!NOTE]
   > Vous devez à présent signer à nouveau le fichier avec *Mage.exe*. Pour plus d’informations, consultez [procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="net-framework-security"></a>Sécurité du .NET Framework
 Si vous installez votre application à partir d’un support hors connexion, tel qu’un CD-ROM, et que l’ordinateur est en ligne, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vérifie tout d’abord l’URL spécifiée par la `<deploymentProvider>` balise dans le manifeste de déploiement pour déterminer si l’emplacement de la mise à jour contient une version plus récente de l’application. Si c’est le cas, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installe l’application directement à partir de là, et non à partir du répertoire d’installation initial, et le Common Language Runtime (CLR) détermine le niveau de confiance de votre application à l’aide de `<deploymentProvider>` . Si l’ordinateur est hors connexion ou `<deploymentProvider>` inaccessible, s' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installe à partir du CD-ROM et le CLR accorde l’approbation en fonction du point d’installation ; pour une installation à partir d’un CD, cela signifie que votre application reçoit une confiance totale. Toutes les mises à jour suivantes héritent de ce niveau de confiance.

 Toutes les [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applications qui utilisent `<deploymentProvider>` doivent déclarer explicitement les autorisations dont ils ont besoin dans leur manifeste d’application, afin que l’application ne reçoive pas différents niveaux d’approbation sur des ordinateurs différents.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Déployer manuellement une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Manifeste de déploiement ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [Sécuriser des applications ClickOnce](../deployment/securing-clickonce-applications.md)
- [Choisir une stratégie de mise à jour ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)