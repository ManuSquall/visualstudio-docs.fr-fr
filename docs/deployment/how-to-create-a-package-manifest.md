---
title: 'Comment : créer un manifeste de Package | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 54c2e6a231ce597e2ec6a3e04cf74521b6c10d2e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-a-package-manifest"></a>Comment : créer un manifeste de package
Pour déployer les composants requis pour votre application, vous pouvez utiliser un package de programme d’amorçage. Un package de programme d’amorçage contient un fichier de manifeste de produit unique, mais un manifeste de package pour chacun des paramètres régionaux. Les fonctionnalités partagées entre plusieurs versions localisées doivent être placée dans le manifeste du produit.  
  
 Pour plus d’informations sur les manifestes de package, consultez [Comment : créer un manifeste de produit](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Création du manifeste de Package  
  
#### <a name="to-create-the-package-manifest"></a>Pour créer le manifeste du package  
  
1.  Créez un répertoire pour le package du programme d’amorçage. Cet exemple utilise C:\package.  
  
2.  Créez un sous-répertoire avec le nom des paramètres régionaux, par exemple en pour l’anglais.  
  
3.  Dans Visual Studio, créez un fichier XML nommé `package.xml`et l’enregistrer dans le dossier C:\package\en.  
  
4.  Ajoutez du code XML pour répertorier le nom du package du programme d’amorçage, la culture pour ce manifeste du package localisé et le contrat de licence facultatif. Le code XML suivant utilise les variables `DisplayName` et `Culture`, qui sont définies dans un élément ultérieur.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Ajoutez du code XML pour répertorier tous les fichiers qui se trouvent dans le répertoire spécifique aux paramètres régionaux. Le code XML suivant utilise un fichier nommé eula.txt qui n’est applicable pour le **en** paramètres régionaux.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Ajoutez le code XML pour définir des chaînes localisables pour le package du programme d’amorçage. Le code XML suivant ajoute des chaînes d’erreur pour les paramètres régionaux en.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Copiez le dossier C:\package vers le répertoire du programme d’amorçage de Visual Studio. Pour Visual Studio 2010, il s’agit de l’annuaire de SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Exemple  
 Le manifeste du package contient des informations de paramètres régionaux spécifiques, telles que les messages d’erreur, les termes du contrat de licence de logiciel et les modules linguistiques.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le schéma de produit et de package](../deployment/product-and-package-schema-reference.md)