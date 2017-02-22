---
title: "Comment&#160;: cr&#233;er un manifeste de package | Microsoft Docs"
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
  - "dépendances, packages du programme d'amorçage personnalisé"
  - "fichiers du package (ClickOnce)"
  - "fichiers du package (Windows Installer)"
  - "composants requis, package du programme d'amorçage personnalisé"
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er un manifeste de package
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour déployer des composants requis pour votre application, vous pouvez utiliser un package du programme d'amorçage.  Un package du programme d'amorçage contient un fichier manifeste de produit unique et un manifeste du package pour chacun des paramètres régionaux.  Les fonctionnalités partagées entre plusieurs versions localisées doivent faire partie du manifeste de produit.  
  
 Pour plus d'informations sur les manifestes de package, consultez [Comment : créer un manifeste de produit](../deployment/how-to-create-a-product-manifest.md).  
  
## Création du manifeste du package  
  
#### Pour créer le manifeste du package  
  
1.  Créez un répertoire pour le package du programme d'amorçage.  Cet exemple utilise C:\\package.  
  
2.  Créez un sous\-répertoire avec le nom des paramètres régionaux, tels que « en » pour Anglais.  
  
3.  Dans Visual Studio, créez un fichier XML nommé `package.xml` et enregistrez\-le dans le dossier C:\\package\\en.  
  
4.  Ajoutez du code XML pour répertorier le nom du package du programme d'amorçage, la culture pour ce manifeste du package localisé et le contrat de licence facultatif.  Le code XML suivant utilise les variables `DisplayName` et `Culture`, définies dans un élément ultérieur.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Ajoutez du code XML pour répertorier tous les fichiers contenus dans le répertoire spécifique aux paramètres régionaux.  Le code XML suivant utilise un fichier nommé eula.txt qui s'applique aux paramètres régionaux **en**.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Ajoutez du code XML afin de définir des chaînes localisables pour le package du programme d'amorçage.  Le code XML suivant ajoute des chaînes d'erreur pour les paramètres régionaux en.  
  
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
  
7.  Copiez le dossier C:\\package vers le répertoire du programme d'amorçage Visual Studio.  Pour Visual Studio 2010, il s'agit du répertoire \\Program Files\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Exemple  
 Le manifeste du package contient des informations spécifiques aux paramètres régionaux, telles que des messages d'erreur, les termes du contrat de licence logiciel et des modules linguistiques.  
  
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
  
## Voir aussi  
 [Référence du schéma de produit et de package](../deployment/product-and-package-schema-reference.md)