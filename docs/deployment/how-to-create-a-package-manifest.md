---
title: Comment créer un manifeste de package | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: dc3a1263136fe4c50b2c7020e1557a7a693691b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382521"
---
# <a name="how-to-create-a-package-manifest"></a>Guide pratique pour créer un manifeste de package
Pour déployer les composants requis pour votre application, vous pouvez utiliser un package du programme d’amorçage. Un package du programme d’amorçage contient un fichier manifeste de produit unique, mais un manifeste de package pour chaque paramètre régional. Les fonctionnalités partagées entre différentes versions localisées doivent être placées dans le manifeste du produit.

 Pour plus d’informations sur les manifestes de produit, consultez [Comment : créer un manifeste de produit](../deployment/how-to-create-a-product-manifest.md).

## <a name="create-the-package-manifest"></a>Créer le manifeste du package

#### <a name="to-create-the-package-manifest"></a>Pour créer le manifeste du package

1. Créez un répertoire pour le package du programme d’amorçage. Cet exemple utilise *C:\package*.

2. Créez un sous-répertoire avec le nom des paramètres régionaux *, par exemple en pour* l’anglais.

3. Dans Visual Studio, créez un fichier XML nommé *package.xml*, puis enregistrez-le dans le dossier *C:\package\en*

4. Ajoutez XML pour répertorier le nom du package du programme d’amorçage, la culture pour ce manifeste du package localisé et le contrat de licence facultatif. Le code XML suivant utilise les variables `DisplayName` et `Culture` , qui sont définies dans un élément ultérieur.

    ```xml
    <Package
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
        Name="DisplayName"
        Culture="Culture"
        LicenseAgreement="eula.txt">
    ```

5. Ajoutez XML pour répertorier tous les fichiers qui se trouvent dans le répertoire spécifique aux paramètres régionaux. Le code XML suivant utilise un fichier nommé *eula.txt* qui s’applique **aux paramètres régionaux** .

    ```xml
    <PackageFiles>
      <PackageFile Name="eula.txt"/>
    </PackageFiles>
    ```

6. Ajoutez XML pour définir des chaînes localisables pour le package du programme d’amorçage. Le code XML suivant ajoute des chaînes d’erreur **pour les paramètres** régionaux.

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

7. Copiez le dossier *C:\package* dans le répertoire du programme d’amorçage de Visual Studio. Pour Visual Studio 2010, il s’agit du répertoire *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*

## <a name="example"></a>Exemple
 Le manifeste du package contient des informations spécifiques aux paramètres régionaux, telles que les messages d’erreur, les termes du contrat de licence logiciel et les modules linguistiques.

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
- [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)