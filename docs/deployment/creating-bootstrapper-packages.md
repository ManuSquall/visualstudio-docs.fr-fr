---
title: Créer des packages de programme d’amorçage
description: En savoir plus sur le programme d’installation et sur l’utilisation de manifestes XML qui spécifient les métadonnées permettant de gérer l’installation des composants ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 007a7f42448ab8026d8acdc262ce5e0dcdd99b28
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877726"
---
# <a name="create-bootstrapper-packages"></a>Créer des packages de programme d’amorçage
Le programme d’installation est un programme d’installation générique qui peut être configuré pour détecter et installer les composants redistribuables, comme les fichiers Windows Installer (*.msi*) et les programmes exécutables. Le programme d'installation est également appelé programme d'amorçage. Il est programmé via un ensemble de manifestes XML qui spécifient les métadonnées permettant de gérer l'installation du composant.  Chaque composant redistribuable, ou condition préalable, qui apparaît dans la boîte de dialogue **composants requis** pour ClickOnce est un package du programme d’amorçage. Un package de programme d'amorçage est un groupe de répertoires et de fichiers qui contiennent des fichiers manifeste qui décrivent la façon dont le composant requis doit être installé.

Le programme d'amorçage détecte d'abord si l'un des composants requis est déjà installé. Si des composants requis ne sont pas installés, le programme d'amorçage commence par afficher les contrats de licence. Une fois que l’utilisateur a accepté les contrats de licence, l’installation des prérequis commence. Si tous les composants requis sont détectés, le programme d'amorçage démarre simplement le programme d'installation de l'application.

## <a name="create-custom-bootstrapper-packages"></a>Créer des packages de programme d’amorçage personnalisés
Vous pouvez générer les manifestes du programme d’amorçage à l’aide de l’éditeur XML dans Visual Studio. Pour voir un exemple de création d’un package de programme d’amorçage, consultez [procédure pas à pas : création d’un programme d’amorçage personnalisé avec une invite de confidentialité](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).

Pour créer un package de programme d’amorçage, vous devez créer un manifeste de produit et, pour chaque version localisée d’un composant, un manifeste de package également.

* Le manifeste de produit, *product.xml*, contient toutes les métadonnées indépendantes du langage pour le package. Il contient les métadonnées communes à toutes les versions localisées du composant redistribuable.  Pour créer ce fichier, consultez [Comment : créer un manifeste de produit](../deployment/how-to-create-a-product-manifest.md).

* Le manifeste du package, *package.xml*, contient des métadonnées spécifiques au langage. Il contient généralement des messages d’erreur localisés. Un composant doit avoir au moins un manifeste du package pour chacune de ses versions localisées. Pour créer ce fichier, consultez [Comment : créer un manifeste de package](../deployment/how-to-create-a-package-manifest.md).

Une fois ces fichiers créés, placez le fichier manifeste du produit dans un dossier nommé en fonction du programme d'amorçage personnalisé. Le fichier manifeste du package est placé dans un dossier nommé en fonction des paramètres régionaux. Par exemple, si le fichier manifeste du package est destiné à une redistribution en anglais, placez le fichier dans un dossier nommé en. Répétez ce processus pour chacun des paramètres régionaux, par exemple ja pour le japonais et de pour l'allemand. Le package de programme d'amorçage personnalisé final peut avoir la structure de dossiers suivante.

```
CustomBootstrapperPackage
  product.xml
  CustomBootstrapper.msi
  de
    eula.rtf
    package.xml
  en
    eula.rtf
    package.xml
  ja
    eula.rtf
    package.xml
```

Ensuite, copiez les fichiers redistribuables dans l’emplacement du dossier du programme d’amorçage. Pour plus d’informations, consultez [Comment : créer un package de programme d’amorçage localisé](../deployment/how-to-create-a-localized-bootstrapper-package.md).

```
*\Program Files (x86)\Microsoft SDKs\ClickOnce Bootstrapper\Packages*
```

ou

```
*<VS Install Path>\MSBuild\Microsoft\VisualStudio\BootstrapperPackages*
```

>[!NOTE]
>Le chemin d’accès indiqué ci-dessus sous le chemin d’installation de Visual Studio fonctionne à partir de la version Visual Studio 2019 Update 7.

Vous pouvez également trouver l’emplacement du dossier du programme d’amorçage à partir de la valeur de **chemin d’accès** dans la clé de Registre suivante :

```
*HKLM\Software\Microsoft\GenericBootstrapper*
```

Sur les systèmes 64 bits, utilisez la clé de Registre suivante :

```
*HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper*
```

Chaque composant redistribuable apparaît dans son propre sous-dossier du répertoire packages. Le manifeste du produit et les fichiers redistribuables doivent être placés dans ce sous-dossier. Les versions localisées du composant et des manifestes de package doivent être placées dans des sous-dossiers nommés en fonction du nom de la culture.

Une fois ces fichiers copiés dans le dossier de programme d’amorçage, le package de programme d’amorçage apparaît automatiquement dans la boîte de dialogue **Composants requis** de Visual Studio. Si votre package de programme d’amorçage personnalisé n’apparaît pas, fermez puis rouvrez la boîte de dialogue **Prérequis**. Pour plus d’informations, consultez [boîte de dialogue composants requis](../ide/reference/prerequisites-dialog-box.md).

Le tableau suivant présente les propriétés qui sont automatiquement remplies par le programme d'amorçage.

|Propriété|Description|
|--------------|-----------------|
|ApplicationName|Le nom de l’application.|
|ProcessorArchitecture|Processeur et bits par mot de la plateforme ciblée par un exécutable. Les valeurs sont notamment les suivantes :<br /><br /> -   Intel<br />-   IA64<br />-   AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Numéro de version des systèmes d'exploitation Microsoft Windows 95, Windows 98 ou Windows ME. La syntaxe de la version est Major.Minor.ServicePack.|
|[VersionNT](/windows/desktop/Msi/versionnt)|Numéro de version des systèmes d'exploitation Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 ou Windows 7. La syntaxe de la version est Major.Minor.ServicePack.|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Version de l’assembly de Windows Installer (msi.dll) à exécuter pendant l’installation.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Cette propriété est définie si l'utilisateur dispose de privilèges d'administrateur. Les valeurs sont true ou false.|
|InstallMode|Le mode d'installation indique l'emplacement d'installation du composant. Les valeurs sont notamment les suivantes :<br /><br /> -   HomeSite : Les prérequis sont installés à partir du site web du fournisseur.<br />-   SpecificSite : Les prérequis sont installés à partir de l’emplacement de votre choix.<br />-   SameSite : Les prérequis sont installés à partir du même emplacement que celui de l’application.|

## <a name="separate-redistributables-from-application-installations"></a>Séparer les fichiers redistribuables des installations d’applications
Vous pouvez empêcher le déploiement de vos fichiers redistribuables dans les projets d'installation. Pour ce faire, créez une liste de composants redistribuables dans le dossier RedistList de votre répertoire du .NET Framework :

`%ProgramFiles%\Microsoft.NET\RedistList`

La liste redistribuable est un fichier XML que vous devez nommer en utilisant le format suivant : *\<Company Name> . \<Component Name>.RedistList.xml*. Ainsi par exemple, si le composant s’appelle Datawidgets et qu’il a été fait par Acme, utilisez *Acme.DataWidgets.RedistList.xml*. Voici un exemple de contenu de la liste de composants redistribuables :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour installer les composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Boîte de dialogue composants requis](../ide/reference/prerequisites-dialog-box.md)
- [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)
- [Utiliser le programme d’amorçage de Visual Studio 2005 pour lancer votre installation](/archive/msdn-magazine/2004/october/visual-studio-2005-bootstrapper-start-kick-your-installation)
