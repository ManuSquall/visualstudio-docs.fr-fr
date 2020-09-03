---
title: 'Comment : inclure des composants requis avec une application ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9639da1f735095f6d04a59d1f2302f822423e006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557676"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Comment : inclure les composants requis avec une application ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Avant de distribuer les logiciels requis avec une application [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], vous devez d'abord télécharger les packages d'installation de ces composants requis sur votre ordinateur de développement. Lorsque vous publiez une application et choisissez **Télécharger les composants requis à partir du même emplacement que mon application**, une erreur se produit si les packages d’installation ne se trouvent pas dans le dossier **packages** .  
  
> [!NOTE]
> Pour ajouter un package d’installation pour le .NET Framework, consultez [Guide de déploiement .NET Framework pour les développeurs](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Pour ajouter un package d’installation à l’aide de Package.xml  
  
1. Dans l’Explorateur de fichiers, ouvrez le dossier **Packages**.  
  
     Par défaut, le chemin d'accès est C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages sur un système 32 bits et C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages sur un système 64 bits.  
  
2. Ouvrez le dossier des composants prérequis que vous voulez ajouter, puis ouvrez le dossier de langage de votre version installée de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (par exemple, **fr** pour le français).  
  
3. Dans le Bloc-notes, ouvrez le fichier **Package.xml**.  
  
4. Localisez l’élément **Name** qui contient `http://go.microsoft.com/fwlink` et copiez l’URL. Incluez la partie **LinkID**.  
  
    > [!NOTE]
    > Si aucun élément **Name** ne contient `http://go.microsoft.com/fwlink` , ouvrez le fichier **Product.xml** dans le dossier racine pour le composant requis et recherchez la chaîne **fwlink** .  
  
    > [!IMPORTANT]
    > Certains composants requis ont plusieurs packages d'installation (par exemple, pour les systèmes 32 bits ou 64 bits). Si plusieurs éléments **Name** contiennent **fwlink**, vous devez répéter les étapes restantes pour chacun d’entre eux.  
  
5. Collez l’URL dans la barre d’adresses de votre navigateur puis, quand vous êtes invité à exécuter ou à enregistrer, choisissez **Enregistrer**.  
  
     Cette étape télécharge le fichier du programme d'installation sur votre ordinateur.  
  
6. Copiez le fichier dans le dossier racine du composant requis.  
  
     Par exemple, pour les composants requis de Windows Installer 4.5, copiez le fichier dans le dossier \Packages\WindowsInstaller4_5.  
  
     Vous pouvez maintenant distribuer le package d'installation avec votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
