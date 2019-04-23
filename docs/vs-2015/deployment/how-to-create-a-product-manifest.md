---
title: 'Procédure : Créer un manifeste de produit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 73e2c3f2c9736fd762a9e763827ed641ea5069f7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092121"
---
# <a name="how-to-create-a-product-manifest"></a>Procédure : Créer un manifeste de produit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour déployer les composants requis pour votre application, vous pouvez créer un package de programme d’amorçage. Un package de programme d’amorçage contient un fichier de manifeste de produit unique, mais un manifeste de package pour chacun des paramètres régionaux. Le manifeste du package contient des aspects spécifiques à la localisation de votre package. Cela inclut des chaînes, des contrats de licence utilisateur final et les modules linguistiques.  
  
 Pour plus d’informations sur les manifestes de produit, consultez [Comment : Créer un manifeste de Package](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Création du manifeste de produit  
  
#### <a name="to-create-the-product-manifest"></a>Pour créer le manifeste de produit  
  
1. Créez un répertoire pour le package de programme d’amorçage. Cet exemple utilise C:\package.  
  
2. Dans Visual Studio, créez un nouveau fichier XML appelé `product.xml`et l’enregistrer dans le dossier C:\package.  
  
3. Ajoutez le code XML suivant pour décrire le code XML de l’espace de noms et de produit pour le package. Remplacez le code de produit par un identificateur unique pour le package.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4. Ajoutez du code XML pour spécifier que le package a une dépendance. Cet exemple utilise une dépendance sur Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5. Ajoutez le code XML pour répertorier tous les fichiers qui se trouvent dans le package de programme d’amorçage. Cet exemple utilise le nom de fichier de package CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6. Copiez ou déplacez le fichier CorePackage.msi dans le dossier C:\package.  
  
7. Ajoutez du code XML pour installer le package à l’aide des commandes de programme d’amorçage. Le programme d’amorçage ajoute automatiquement le **/qn** indicateur au fichier .msi, qui va installer en mode silencieux. Si le fichier est un .exe, le programme d’amorçage exécute le fichier .exe à l’aide de l’interpréteur de commandes. Le code XML suivant ne montre aucun argument pour CorePackage.msi, mais vous pouvez placer l’argument de ligne de commande dans l’attribut Arguments.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8. Ajoutez le code XML suivant pour vérifier si ce package du programme d’amorçage est installé. Remplacez le code de produit par le GUID pour le composant redistribuable.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Ajoutez du code XML pour modifier le comportement du programme d’amorçage selon si le composant de programme d’amorçage est déjà installé. Si le composant est installé, le package de programme d’amorçage ne s’exécute pas. Le code XML suivant vérifie si l’utilisateur actuel est un administrateur, car ce composant requiert des privilèges d’administrateur.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Ajoutez du code XML pour définir les codes de sortie si l’installation a réussi et si un redémarrage est nécessaire. Le code XML suivant montre que la échouent et FailReboot exit codes, qui indiquent que le programme d’amorçage ne continuera pas l’installation des packages.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Ajoutez le code XML suivant pour mettre fin à la section pour les commandes de programme d’amorçage.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Déplacer le dossier C:\package vers le répertoire du programme d’amorçage de Visual Studio. Pour Visual Studio 2010, il s’agit de l’annuaire de SDKs\Windows\v7.0A\Bootstrapper\Packages \Program Files\Microsoft.  
  
## <a name="example"></a>Exemple  
 Le manifeste de produit contient des instructions d’installation de composants requis personnalisés.  
  
```  
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
 [Informations de référence sur le schéma de produit et de package](../deployment/product-and-package-schema-reference.md)
