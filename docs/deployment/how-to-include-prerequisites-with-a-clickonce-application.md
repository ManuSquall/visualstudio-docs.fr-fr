---
title: 'Comment : inclure les composants requis avec une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a31058893e09de2c945cc253374a55c53f277110
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620003"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Guide pratique pour inclure les composants requis avec une application ClickOnce
Avant de distribuer les logiciels requis avec une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous devez d'abord télécharger les packages d'installation de ces composants requis sur votre ordinateur de développement. Quand vous publiez une application et que vous choisissez **Télécharger les composants requis à partir de l’emplacement de mon application**, une erreur se produit lorsque les packages d’installation ne sont pas dans le dossier **Packages**.

> [!NOTE]
>  Pour ajouter un package d’installation pour le .NET Framework, consultez [Guide de déploiement de .NET Framework pour les développeurs](/dotnet/framework/deployment/deployment-guide-for-developers).

##  <a name="Package"></a> Pour ajouter un package d’installation à l’aide de Package.xml

1. Dans l’Explorateur de fichiers, ouvrez le dossier **Packages**.

    Par défaut, le chemin d’accès est *C:\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* sur un système 32 bits et *C:\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages* sur un système 64 bits.

2. Ouvrez le dossier des composants prérequis que vous voulez ajouter, puis ouvrez le dossier de langage de votre version installée de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (par exemple, **fr** pour le français).

3. Dans le Bloc-notes, ouvrez le fichier *Package.xml*.

4. Recherchez le **nom** élément contenant **http://go.microsoft.com/fwlink**, puis copiez l’URL. Incluez la partie **LinkID**.

   > [!NOTE]
   >  Si aucun **nom** élément contient **http://go.microsoft.com/fwlink**, ouvrez le **Product.xml** de fichiers dans le dossier racine pour les composants requis et recherchez le **fwlink** chaîne.

   > [!IMPORTANT]
   >  Certains composants requis ont plusieurs packages d'installation (par exemple, pour les systèmes 32 bits ou 64 bits). Si plusieurs éléments **Name** contiennent **fwlink**, vous devez répéter les étapes restantes pour chacun d’entre eux.

5. Collez l’URL dans la barre d’adresses de votre navigateur puis, quand vous êtes invité à exécuter ou à enregistrer, choisissez **Enregistrer**.

    Cette étape télécharge le fichier du programme d'installation sur votre ordinateur.

6. Copiez le fichier dans le dossier racine du composant requis.

    Par exemple, pour les composants requis de Windows Installer 4.5, copiez le fichier dans le dossier *\Packages\WindowsInstaller4_5*.

    Vous pouvez maintenant distribuer le package d'installation avec votre application.

## <a name="see-also"></a>Voir aussi
- [Comment : installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)