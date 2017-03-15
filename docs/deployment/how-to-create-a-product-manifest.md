---
title: "Comment&#160;: cr&#233;er un manifeste de produit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "dépendances, package du programme d'amorçage personnalisé"
  - "composants requis, package du programme d'amorçage personnalisé"
  - "fichiers de produit (ClickOnce)"
  - "fichiers du produit (Windows Installer)"
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: cr&#233;er un manifeste de produit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour déployer des composants requis pour votre application, vous pouvez créer un package du programme d'amorçage.  Un package du programme d'amorçage contient un fichier manifeste de produit unique et un manifeste du package pour chacun des paramètres régionaux.  Le manifeste du package contient des aspects spécifiques à la localisation de votre package.  Cela inclut des chaînes, des contrats de Licence Utilisateur Final et les modules linguistiques.  
  
 Pour plus d'informations sur les manifestes de produit, consultez [Comment : créer un manifeste de package](../deployment/how-to-create-a-package-manifest.md).  
  
## Création du manifeste de produit  
  
#### Pour créer le manifeste de produit  
  
1.  Créez un répertoire pour le package du programme d'amorçage.  Cet exemple utilise C:\\package.  
  
2.  Dans Visual Studio, créez un fichier XML appelé `product.xml` et enregistrez\-le dans le dossier C:\\package.  
  
3.  Ajoutez le XML suivant afin de décrire l'espace de noms XML et le code du produit pour le package.  Remplacez le code du produit par un identificateur unique pour le package.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Ajoutez du code XML pour spécifier que le package a une dépendance.  Cet exemple utilise une dépendance à Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Ajoutez du code XML pour répertorier tous les fichiers contenus dans le package du programme d'amorçage.  Cet exemple utilise le nom de fichier CorePackage.msi pour le package.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Copiez ou déplacez le fichier CorePackage.msi vers le dossier C:\\package.  
  
7.  Ajoutez du code XML pour installer le package à l'aide des commandes du programme d'amorçage.  Le programme d'amorçage ajoute automatiquement l'indicateur **\/qn** au fichier .msi, qui s'installera silencieusement.  Si le fichier est un .exe, le programme d'amorçage exécute le fichier .exe à l'aide du shell.  Le code XML suivant ne montre aucun argument pour CorePackage.msi, mais vous pouvez placer l'argument de ligne de commande dans l'attribut Arguments.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Ajoutez le code XML suivant pour vérifier si ce package du programme d'amorçage est installé.  Remplacez le code du produit par le GUID pour le composant redistribuable.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Ajoutez du code XML pour modifier le comportement du programme d'amorçage selon que le composant du programme d'amorçage est déjà installé ou non.  Si le composant est installé, le package du programme d'amorçage ne s'exécute pas.  Le code XML suivant vérifie si l'utilisateur actuel est un administrateur, car ce composant requiert des privilèges d'administrateur.  
  
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
  
10. Ajoutez du code XML pour définir des codes de sortie si l'installation aboutit et si un redémarrage est nécessaire.  Le code XML suivant montre les codes de sortie Fail et FailReboot, qui indiquent que le programme d'amorçage ne continuera pas à installer des packages.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Ajoutez le code XML suivant afin de terminer la section pour les commandes du programme d'amorçage.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Déplacez le dossier C:\\package vers le répertoire du programme d'amorçage Visual Studio.  Pour Visual Studio 2010, il s'agit du répertoire \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Exemple  
 Le manifeste de produit contient des instructions d'installation pour les composants requis personnalisés.  
  
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
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)