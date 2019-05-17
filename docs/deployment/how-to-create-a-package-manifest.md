---
title: 'Procédure : Créer un manifeste de Package | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8083ca9a8d3025b1760edde96279a0cd557f722
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899738"
---
# <a name="how-to-create-a-package-manifest"></a>Procédure : Créer un manifeste de package
Pour déployer les composants requis pour votre application, vous pouvez utiliser un package de programme d’amorçage. Un package de programme d’amorçage contient un fichier de manifeste de produit unique, mais un manifeste de package pour chacun des paramètres régionaux. Les fonctionnalités partagées entre les différentes versions localisées doit être placé dans le manifeste de produit.

 Pour plus d’informations sur les manifestes de produit, consultez [Comment : Créer un manifeste de produit](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Créer le manifeste du package

#### <a name="to-create-the-package-manifest"></a>Pour créer le manifeste du package

1. Créez un répertoire pour le package de programme d’amorçage. Cet exemple utilise *C:\package*.

2. Créez un sous-répertoire avec le nom des paramètres régionaux, telles que *en* pour l’anglais.

3. Dans Visual Studio, créez un fichier XML nommé *package.xml*et enregistrez-le dans le *C:\package\en* dossier.

4. Ajoutez du code XML pour répertorier le nom du package du programme d’amorçage, la culture pour ce manifeste de package localisé et le contrat de licence facultatif. Le code XML suivant utilise les variables `DisplayName` et `Culture`, qui sont définies dans un élément ultérieur.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Ajoutez du code XML pour répertorier tous les fichiers qui se trouvent dans le répertoire de paramètres régionaux spécifiques. Le code XML suivant utilise un fichier nommé *eula.txt* qui s’applique à la **en** paramètres régionaux.

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Ajoutez le code XML pour définir des chaînes localisables pour le package de programme d’amorçage. Le code XML suivant ajoute des chaînes d’erreur pour le **en** paramètres régionaux.

    ```xml
      <Strings>
        <String Name="DisplayName">Custom Bootstrapper Package</String>
        <String Name="CultureName">en</String>
        <String Name="NotAnAdmin">You must be an administrator to install
    this package.</String>
        <String Name="GeneralFailure">A general error has occurred while
    installing this package.</String>
    </Strings>
    ```

7. Copie le *C:\package* dossier dans le répertoire du programme d’amorçage de Visual Studio. Pour Visual Studio 2010, il s’agit du *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages* directory.

## <a name="example"></a>Exemple
 Le manifeste du package contient des informations de paramètres régionaux spécifiques, tels que les messages d’erreur, les termes du contrat de licence de logiciel et les modules linguistiques.

```xml
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
- [Informations de référence sur le schéma de produit et de package](../deployment/product-and-package-schema-reference.md)