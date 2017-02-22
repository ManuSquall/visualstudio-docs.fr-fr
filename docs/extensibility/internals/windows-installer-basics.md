---
title: "Principes fondamentaux de Windows Installer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Programme d’installation de Windows, les packages VS"
  - "VSPackages, les principes fondamentaux de Windows Installer"
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Principes fondamentaux de Windows Installer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le programme d’installation de Windows installe et désinstalle des applications ou des logiciels sur l’ordinateur d’un utilisateur, effectuer ces tâches dans des unités appelées des composants de Windows Installer \(parfois appelés WICs ou composants uniquement\). Un GUID identifie chaque WIC, qui est l’unité de base de l’installation et le décompte de références pour les installations à l’aide de Windows Installer.  
  
 Pour obtenir une documentation complète de Windows Installer, consultez la rubrique Platform SDK, [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## Création d’un VSPackage  
 Le programme d’installation de Windows utilise des packages d’installation, qui contiennent des informations Windows Installer a besoin pour installer, désinstaller ou réparer un produit et pour exécuter l’interface utilisateur de configuration \(UI\). Chaque package d’installation inclut un fichier .msi, qui contient une base de données de l’installation, un flux d’informations résumées et des flux de données pour différentes parties de l’installation. Pour utiliser le programme d’installation, vous devez créer une installation. Étant donné que le programme d’installation organise les installations autour du concept de composants et stocke des informations sur l’installation dans une base de données relationnelle, le processus de création d’un package d’installation largement implique les étapes suivantes :  
  
1.  Planifiez votre installation de création pour prendre en charge votre contrôle de version et les stratégies de côte\-à\-côte.  
  
2.  Identifier les fonctionnalités à présenter aux utilisateurs.  
  
3.  Organiser le VSPackage et les dépendances de composants.  
  
4.  Remplir la base de données de l’installation avec les informations.  
  
5.  Valider le package d’installation.  
  
 Cette documentation concerne principalement les premier et troisième les étapes du processus. Au cours de ces étapes vous organisez vos fonctionnalités VSPackage en WICs afin de vous pouvez le cadre de votre contrôle de version et la maintenance de stratégie pour prendre en compte les versions suivantes de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Les trois étapes sont traitées en détail dans la documentation de Windows Installer dans le SDK de plate\-forme.  
  
## Termes clés  
 Voici les définitions des termes clés liés à la technologie Windows Installer.  
  
 Ressource  
 Fichiers, clés de Registre, des raccourcis, ou, etc. qui peuvent être installés sur un ordinateur. Ces ressources sont regroupées logiquement dans des composants de Windows Installer.  
  
 Composant de programme d’installation de Windows \(WIC\)  
 L’unité de base d’installation qui représente un regroupement logique des ressources connexes qui sont installés et désinstallés en tant qu’unité. Composants de Windows Installer sont identifiés par un ID de composant unique, ou GUID. En outre, Windows Installer conserve son décompte de références au niveau du WIC. Pour une flexibilité maximale de contrôle de version, inclure pas plus d’une ressource principale, par exemple une DLL, dans un WIC donné. Notez qu’après avoir identifié et remplir un WIC, lui donner un GUID et le déployer, vous ne pouvez pas modifier sa composition. Pour plus d’informations, consultez [organiser des Applications en composants](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Package \(package redistribuable\)  
 Une unité de déploiement qui se compose d’un fichier .msi et des fichiers de source externe à laquelle ce fichier peut pointer. Un package contient toutes les informations nécessaires pour exécuter l’interface utilisateur et à installer ou désinstaller l’application Windows Installer.  
  
 fichier .msi  
 Un fichier de stockage structuré COM contenant les instructions et les données requises pour installer une application. Chaque package contient au moins un fichier .msi. Le fichier .msi contient la base de données du programme d’installation, un flux d’informations résumées et éventuellement une ou plusieurs transformations et des fichiers source internes. Installation des fichiers peuvent soit être compressés dans un fichier CAB et stockés dans un flux de données dans le fichier .msi ou stockées, compressés ou décompressés, en dehors du fichier .msi sur le support source. Pour plus d’informations, consultez [Extensions de fichier Windows Installer](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## Mise en œuvre de règles Windows Installer  
 Deux ensembles de règles déterminent le déploiement de ressources via les composants de votre installation. Un ensemble de règles est géré par le programme d’installation de Windows, alors que vous devez appliquer le second ensemble en tant qu’auteur de l’installation.  
  
> [!NOTE]
>  L’application de règles Windows Installer se produit uniquement si vous exécutez une validation de votre fichier .msi. Néanmoins, vous êtes indispensable pour traiter ces règles comme meilleures pratiques. Pour plus d’informations, consultez [validation d’une base de données d’Installation](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) et [Validation du Package](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### Règles appliquée par le programme d’installation  
  
-   Tous les fichiers dans un composant donné doivent être installés dans le même répertoire. À l’inverse, les fichiers installés pour séparer les dossiers doivent appartenir pour séparer les composants.  
  
-   Il peut y avoir qu’un seul chemin d’accès clé par composant. Le chemin d’accès clé est simplement une fichier ou clé de Registre qui représente le composant entier.  
  
#### Responsabilités du fournisseur de composant  
  
-   Les deux ressources qui peut être fourni séparément dans les versions ultérieures doivent exister dans des composants séparés. Ressources doivent être regroupées dans le même composant que lorsque vous êtes certain que ces ressources ne sera jamais séparément. En fait, il est recommandé que toutes les ressources principales \(DLL, par exemple\) existent toujours dans WICs distincts. Pour plus d’informations, consultez [définition des composants de programme d’installation](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Aucune ressource version ne doit expédier jamais dans plusieurs WIC.  
  
## Voir aussi  
 [Que se passe\-t\-il si les règles de composant sont interrompues ?](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)