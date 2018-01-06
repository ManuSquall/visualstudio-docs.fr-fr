---
title: "Comment : intégrer des composants requis avec une Application ClickOnce | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 4fbab9bacc8c5272588a4b2dfe819650bfc6110f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Comment : inclure les composants requis avec une application ClickOnce
Avant de distribuer les logiciels requis avec une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous devez d'abord télécharger les packages d'installation de ces composants requis sur votre ordinateur de développement. Lorsque vous publiez une application et choisissez **télécharger les composants requis à partir du même emplacement que mon application**, une erreur se produit si les packages d’installation ne figurent pas dans le **Packages** dossier.  
  
> [!NOTE]
>  Pour ajouter un package d’installation pour le .NET Framework, consultez [Guide de déploiement de .NET Framework pour les développeurs](http://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx).  
  
##  <a name="Package"></a>Pour ajouter un package d’installation à l’aide de Package.xml  
  
1.  Dans l’Explorateur de fichiers, ouvrez le **Packages** dossier.  
  
     Par défaut, le chemin d’accès est C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages sur un système 32 bits et C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages sur un système 64 bits.  
  
2.  Ouvrez le dossier des composants prérequis que vous souhaitez ajouter, puis ouvrez le dossier de langue de votre version installée de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (par exemple, **en** pour l’anglais).  
  
3.  Dans le bloc-notes, ouvrez le **Package.xml** fichier.  
  
4.  Recherchez le **nom** élément contenant **http://go.microsoft.com/fwlink**, puis copiez l’URL. Inclure le **LinkID** partie.  
  
    > [!NOTE]
    >  Si aucun **nom** élément contient **http://go.microsoft.com/fwlink**, ouvrez le **Product.xml** de fichiers dans le dossier racine pour les composants requis et recherchez le  **fwlink** chaîne.  
  
    > [!IMPORTANT]
    >  Certains composants requis ont plusieurs packages d'installation (par exemple, pour les systèmes 32 bits ou 64 bits). Si plusieurs **nom** contiennent des éléments **fwlink**, vous devez répéter les étapes restantes pour chacun d’eux.  
  
5.  Collez l’URL dans la barre d’adresses de votre navigateur et, lorsque vous êtes invité à exécuter ou enregistrer, choisissez **enregistrer**.  
  
     Cette étape télécharge le fichier du programme d'installation sur votre ordinateur.  
  
6.  Copiez le fichier dans le dossier racine du composant requis.  
  
     Par exemple, pour les composants requis de Windows Installer 4.5, copiez le fichier dans le dossier \Packages\WindowsInstaller4_5.  
  
     Vous pouvez maintenant distribuer le package d'installation avec votre application.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour installer des composants prérequis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)