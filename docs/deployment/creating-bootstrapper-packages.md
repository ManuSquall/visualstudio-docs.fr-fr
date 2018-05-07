---
title: Créer des packages de programme d’amorçage
ms.custom: ''
ms.date: 05/02/2018
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 29faeafb56c5c077602a3dbcba5ecbb6bb2ab118
ms.sourcegitcommit: 56018fb1f52f17bf35ae2ce71c50c763486e6173
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="create-bootstrapper-packages"></a>Créer des packages de programme d’amorçage
Le programme d'installation est un programme d'installation générique qui peut être configuré pour détecter et installer les composants redistribuables tels que les fichiers Windows Installer (msi) et les programmes exécutables. Le programme d'installation est également appelé programme d'amorçage. Il est programmé via un ensemble de manifestes XML qui spécifient les métadonnées permettant de gérer l'installation du composant.  Chaque composant redistribuable, ou une condition préalable, est un package de programme d’amorçage. Un package de programme d'amorçage est un groupe de répertoires et de fichiers qui contiennent des fichiers manifeste qui décrivent la façon dont le composant requis doit être installé. 
  
Le programme d'amorçage détecte d'abord si l'un des composants requis est déjà installé. Si des composants requis ne sont pas installés, le programme d'amorçage commence par afficher les contrats de licence. Une fois que l'utilisateur a accepté les contrats de licence, l'installation des composants requis s'exécute. Si tous les composants requis sont détectés, le programme d'amorçage démarre simplement le programme d'installation de l'application.  
  
## <a name="create-custom-bootstrapper-packages"></a>Créer des packages de programme d’amorçage personnalisé  
Vous pouvez générer les manifestes de programme d’amorçage à l’aide de l’éditeur XML dans Visual Studio. Pour voir un exemple de création d’un package de programme d’amorçage, consultez [procédure pas à pas : création d’un programme d’amorçage personnalisé avec une invite de confidentialité](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).  
  
Pour créer un package de programme d’amorçage, vous devez créer un manifeste de produit et, pour chaque version localisée d’un composant, un manifeste du package.
  
* Le manifeste du produit, *product.xml*, contient toutes les métadonnées indépendantes du langage pour le package. Il contient les métadonnées communes à toutes les versions localisées du composant redistribuable.  Pour créer ce fichier, consultez [Comment : créer un manifeste de produit](../deployment/how-to-create-a-product-manifest.md).
  
* Le manifeste du package, *package.xml*, contient les métadonnées spécifiques au langage ; il contient généralement des messages d’erreur localisé. Un composant doit avoir au moins un manifeste du package pour chacune de ses versions localisées. Pour créer ce fichier, consultez [Comment : créer un manifeste de Package](../deployment/how-to-create-a-package-manifest.md).
  
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
  
Ensuite, copiez les fichiers redistribuables dans l’emplacement du dossier du programme d’amorçage. Pour plus d'informations, consultez [How to: Create a Localized Bootstrapper Package](../deployment/how-to-create-a-localized-bootstrapper-package.md).
 
    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
    
ou  
    
    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*
  
Vous pouvez également déterminer l'emplacement du dossier de programme d'amorçage à partir de la valeur **Path** de la clé de Registre suivante :  
  
    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*
  
Sur les systèmes 64 bits, utilisez la clé de Registre suivante :  
  
    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*
  
Chaque composant redistribuable apparaît dans son propre sous-dossier du répertoire packages. Le produit de manifeste et redistribuable de fichiers doivent être placés dans ce sous-dossier. Les versions localisées des manifestes de composant et de package doivent être placées dans les sous-dossiers nommés en fonction du nom de Culture.  
  
Une fois ces fichiers sont copiés dans le dossier du programme d’amorçage, le package du programme d’amorçage apparaît automatiquement dans Visual Studio **conditions préalables** boîte de dialogue. Si votre package de programme d’amorçage personnalisé n’apparaît pas, fermez et réouvrez la **conditions préalables** boîte de dialogue. Pour plus d'informations, consultez [Prerequisites Dialog Box](../ide/reference/prerequisites-dialog-box.md).  
  
Le tableau suivant présente les propriétés qui sont automatiquement remplies par le programme d'amorçage.  
  
|Propriété|Description|  
|--------------|-----------------|  
|ApplicationName|Nom de l'application.|  
|ProcessorArchitecture|Processeur et bits par mot de la plateforme ciblée par un exécutable. Les valeurs sont notamment les suivantes :<br /><br /> -Intel<br />-IA64<br />-AMD64|  
|[Version9x](https://msdn.microsoft.com/en-us/library/aa372490\(v=vs.140\).aspx)|Numéro de version des systèmes d'exploitation Microsoft Windows 95, Windows 98 ou Windows ME. La syntaxe de la version est Major.Minor.ServicePack.|  
|[VersionNT](https://msdn.microsoft.com/en-us/library/aa372495\(v=vs.140\).xaspx)|Numéro de version des systèmes d'exploitation Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 ou Windows 7. La syntaxe de la version est Major.Minor.ServicePack.|  
|[VersionMSI](https://msdn.microsoft.com/en-us/library/aa372493\(v=vs.140\).aspx)|Version de l'assembly Windows Installer (msi.dll) exécuté durant l'installation.|  
|[AdminUser](https://msdn.microsoft.com/en-us/library/aa367545\(v=vs.140\).aspx)|Cette propriété est définie si l'utilisateur dispose de privilèges d'administrateur. Les valeurs sont true ou false.|  
|InstallMode|Le mode d'installation indique l'emplacement d'installation du composant. Les valeurs sont notamment les suivantes :<br /><br /> Conditions préalables requises - HomeSite - sont installés à partir du site du fournisseur Web.<br />Conditions préalables de - SpecificSite - sont installés à partir de l’emplacement que vous sélectionnez.<br />Conditions préalables de - SameSite - sont installés dans le même emplacement que l’application.|  
  
## <a name="separating-redistributables-from-application-installations"></a>Séparation des composants redistribuables des installations des applications  
Vous pouvez empêcher le déploiement de vos fichiers redistribuables dans les projets d'installation. Pour ce faire, créez une liste de composants redistribuables dans le dossier RedistList de votre répertoire du .NET Framework :  
  
`%ProgramFiles%\Microsoft.NET\RedistList`  
  
La liste de composants redistribuables est un fichier XML que vous devez nommer en respectant le format suivant : *Nom de la société*.*Nom du composant*.RedistList.xml. Ainsi, par exemple, si le composant s’appelle Datawidgets fait par Acme, utilisez *Acme.DataWidgets.RedistList.xml*. Voici un exemple de contenu de la liste de composants redistribuables :  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<FileList Redist="Acme.DataWidgets" >  
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />  
</FileList>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour installer des composants requis avec une application ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Boîte de dialogue composants requis](../ide/reference/prerequisites-dialog-box.md)   
 [Référence du schéma de Package et de produit](../deployment/product-and-package-schema-reference.md)   
 [Utilisez le Visual Studio 2005 du programme d’amorçage pour démarrer rapidement votre Installation](http://go.microsoft.com/fwlink/?LinkId=107537)