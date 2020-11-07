---
title: Créer un manifeste de produit | Microsoft Docs
description: Découvrez comment déployer des composants requis pour votre application ClickOnce avec un package qui contient un manifeste de produit unique et un manifeste de package pour chaque paramètre régional.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab7156635914d46dfc1849717d29ac0416e2d9fa
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351217"
---
# <a name="how-to-create-a-product-manifest"></a>Guide pratique pour créer un manifeste de produit
Pour déployer des composants requis pour votre application, vous pouvez créer un package de programme d’amorçage. Un package du programme d’amorçage contient un fichier manifeste de produit unique, mais un manifeste de package pour chaque paramètre régional. Le manifeste du package contient des aspects spécifiques de la localisation de votre package. Cela comprend les chaînes, les contrats de licence utilisateur final et les modules linguistiques.

 Pour plus d’informations sur les manifestes de package, consultez [Comment : créer un manifeste de package](../deployment/how-to-create-a-package-manifest.md).

## <a name="create-the-product-manifest"></a>Créer le manifeste de produit

#### <a name="to-create-the-product-manifest"></a>Pour créer le manifeste de produit

1. Créez un répertoire pour le package du programme d’amorçage. Cet exemple utilise C:\package.

2. Dans Visual Studio, créez un nouveau fichier XML appelé *product.xml* , puis enregistrez-le dans le dossier *C:\package*

3. Ajoutez le code XML suivant pour décrire l’espace de noms XML et le code de produit pour le package. Remplacez le code du produit par un identificateur unique pour le package.

    ```xml
    <Product
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
    ProductCode="Custom.Bootstrapper.Package">
    ```

4. Ajoutez XML pour spécifier que le package a une dépendance. Cet exemple utilise une dépendance sur Microsoft Windows Installer 3,1.

    ```xml
    <RelatedProducts>
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
      </RelatedProducts>
    ```

5. Ajoutez XML pour répertorier tous les fichiers qui se trouvent dans le package du programme d’amorçage. Cet exemple utilise le nom du fichier de package *CorePackage.msi*.

    ```xml
    <PackageFiles>
        <PackageFile Name="CorePackage.msi"/>
    </PackageFiles>
    ```

6. Copiez ou déplacez le fichier *CorePackage.msi* dans le dossier *C:\package* .

7. Ajoutez du code XML pour installer le package à l’aide des commandes du programme d’amorçage. Le programme d’amorçage ajoute automatiquement l’indicateur **/qn** au fichier *. msi* , qui s’installe en mode silencieux. Si le fichier est un fichier *. exe* , le programme d’amorçage exécute le fichier *. exe* à l’aide de l’interpréteur de commandes. Le code XML suivant n’affiche aucun argument pour *CorePackage.msi* , mais vous pouvez placer l’argument de ligne de commande dans l' `Arguments` attribut.

    ```xml
    <Commands>
        <Command PackageFile="CorePackage.msi" Arguments="">
    ```

8. Ajoutez le code XML suivant pour vérifier si ce package du programme d’amorçage est installé. Remplacez le code du produit par le GUID du composant redistribuable.

    ```xml
    <InstallChecks>
        <MsiProductCheck
            Property="IsMsiInstalled"
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
    </InstallChecks>
    ```

9. Ajoutez du code XML pour modifier le comportement du programme d’amorçage en fonction de si le composant de programme d’amorçage est déjà installé. Si le composant est installé, le package du programme d’amorçage ne s’exécute pas. Le code XML suivant vérifie si l’utilisateur actuel est un administrateur, car ce composant requiert des privilèges d’administrateur.

    ```xml
    <InstallConditions>
        <BypassIf
           Property="IsMsiInstalled"
           Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
            Compare="ValueNotEqualTo" Value="True"
            String="NotAnAdmin"/>
    </InstallConditions>
    ```

10. Ajoutez XML pour définir les codes de sortie si l’installation réussit et si un redémarrage est nécessaire. Le code XML suivant illustre les codes de sortie Fail et FailReboot, qui indiquent que le programme d’amorçage ne continuera pas à installer les packages.

    ```xml
    <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
    </ExitCodes>
    ```

11. Ajoutez le code XML suivant pour terminer la section relative aux commandes du programme d’amorçage.

    ```xml
        </Command>
    </Commands>
    ```

12. Déplacez le dossier *C:\package* vers le répertoire du programme d’amorçage de Visual Studio. Pour Visual Studio 2010, il s’agit du répertoire *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages*

## <a name="example"></a> Exemple
 Le manifeste du produit contient des instructions d’installation pour les composants requis personnalisés.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Product
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  ProductCode="Custom.Bootstrapper.Package">

  <RelatedProducts>
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />
  </RelatedProducts>

  <PackageFiles>
    <PackageFile Name="CorePackage.msi"/>
  </PackageFiles>

  <InstallChecks>
    <MsiProductCheck Product="IsMsiInstalled"
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>
  </InstallChecks>

  <Commands>
    <Command PackageFile="CorePackage.msi" Arguments="">

      <InstallConditions>
        <BypassIf Property="IsMsiInstalled"
          Compare="ValueGreaterThan" Value="0"/>
        <FailIf Property="AdminUser"
          Compare="ValueNotEqualTo" Value="True"
         String="NotAnAdmin"/>
      </InstallConditions>

      <ExitCodes>
        <ExitCode Value="0" Result="Success"/>
        <ExitCode Value="1641" Result="SuccessReboot"/>
        <ExitCode Value="3010" Result="SuccessReboot"/>
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>
      </ExitCodes>
    </Command>
  </Commands>
</Product>
```

## <a name="see-also"></a>Voir aussi
- [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)