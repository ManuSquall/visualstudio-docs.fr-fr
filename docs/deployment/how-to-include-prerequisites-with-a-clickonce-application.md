---
title: 'Procédure : Inclure les composants requis avec une Application ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcef749068dfb1f13e5b08160a70dda168b771ee
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232851"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Procédure : Inclure des prérequis dans une application ClickOnce
Avant de distribuer les logiciels requis avec une application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], vous devez d'abord télécharger les packages d'installation de ces composants requis sur votre ordinateur de développement. Quand vous publiez une application et que vous choisissez **Télécharger les composants requis à partir de l’emplacement de mon application**, une erreur se produit lorsque les packages d’installation ne sont pas dans le dossier **Packages**.

> [!NOTE]
>  Pour ajouter un package d’installation pour le .NET Framework, consultez [Guide de déploiement de .NET Framework pour les développeurs](/dotnet/framework/deployment/deployment-guide-for-developers).

##  <a name="Package"></a> Pour ajouter un package d’installation à l’aide de Package.xml

1. Dans l’Explorateur de fichiers, ouvrez le dossier **Packages**.

    Par défaut, le chemin d’accès est `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\`.

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
- [Procédure : Installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
