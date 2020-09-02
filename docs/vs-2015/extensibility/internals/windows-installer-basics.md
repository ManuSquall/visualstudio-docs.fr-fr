---
title: Notions de base de Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4693654e12dc37209cb92e3e2ba95bde8bd13e77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687677"
---
# <a name="windows-installer-basics"></a>Éléments de base de Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le Windows Installer installe et désinstalle des applications ou des produits logiciels sur l’ordinateur d’un utilisateur, en effectuant ces tâches dans des unités appelées Windows Installer composants (parfois appelés WICs ou simplement composants). Un GUID identifie chaque WIC, qui est l’unité de base de l’installation et le décompte de références pour les configurations à l’aide de Windows Installer.  
  
 Pour obtenir une documentation complète sur le Windows Installer, consultez la rubrique Kit de développement logiciel (SDK) de la plateforme, [Windows Installer](/previous-versions/2kt85ked(v=vs.120)).  
  
## <a name="authoring-a-vspackage"></a>Création d’un VSPackage  
 Windows Installer utilise des packages d’installation, qui contiennent des informations dont Windows Installer a besoin pour installer, désinstaller ou réparer un produit et pour exécuter l’interface utilisateur du programme d’installation. Chaque package d’installation inclut un fichier. msi, qui contient une base de données d’installation, un flux d’informations de synthèse et des flux de données pour différentes parties de l’installation. Pour utiliser le programme d’installation, vous devez créer une installation. Étant donné que le programme d’installation organise les installations autour du concept de composants et stocke les informations relatives à l’installation dans une base de données relationnelle, le processus de création d’un package d’installation comprend les étapes suivantes :  
  
1. Planifiez la création de votre configuration pour prendre en charge votre version et vos stratégies côte à côte.  
  
2. Identifiez les fonctionnalités à présenter aux utilisateurs.  
  
3. Organisez le VSPackage et les dépendances en composants.  
  
4. Remplissez la base de données d’installation avec les informations.  
  
5. Validez le package d’installation.  
  
   Cette documentation concerne principalement la première et la troisième étape du processus. Au cours de ces étapes, vous organisez vos fonctionnalités VSPackage dans WICs afin de pouvoir décadrer votre stratégie de gestion des versions et de maintenance pour prendre en compte les versions ultérieures de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Les trois étapes restantes sont décrites en détail dans Windows Installer documentation du kit de développement Platform SDK.  
  
## <a name="key-terms"></a>Termes clés  
 Voici les définitions des termes clés associés à la technologie Windows Installer.  
  
 Ressource  
 Fichiers, clés de Registre, raccourcis, etc., qui peuvent être installés sur un ordinateur. Ces ressources sont regroupées logiquement dans des composants de Windows Installer.  
  
 Composant Windows Installer (WIC)  
 Unité d’installation de base représentant un regroupement logique de ressources associées qui sont installées et désinstallées en tant qu’unité. Les composants de Windows Installer sont identifiés par un ID de composant unique ou un GUID. En outre, Windows Installer conserve son décompte de références au niveau du WIC. Pour une flexibilité maximale de gestion des versions, n’incluez qu’une seule ressource principale, telle qu’une DLL, dans un WIC donné. Notez qu’après avoir identifié et renseigné un WIC, lui avoir un GUID et le déployer, vous ne pouvez pas modifier sa composition. Pour plus d’informations, consultez [Organisation des applications dans des composants](https://msdn.microsoft.com/library/aa370561.aspx).  
  
 Package (package Redist)  
 Unité de déploiement qui se compose d’un fichier. msi et de fichiers sources externes dans lesquels ce fichier peut pointer. Un package contient toutes les informations dont Windows Installer a besoin pour exécuter l’interface utilisateur et installer ou désinstaller l’application.  
  
 Fichier. msi  
 Fichier de stockage structuré COM contenant les instructions et les données requises pour installer une application. Chaque package contient au moins un fichier. msi. Le fichier. msi contient la base de données du programme d’installation, un flux d’informations de synthèse et éventuellement une ou plusieurs transformations et des fichiers sources internes. Les fichiers à installer peuvent être compressés dans un fichier CAB et stockés dans un flux du fichier. msi, ou stockés, compressés ou non compressés, en dehors du fichier. msi sur le support source. Pour plus d’informations, consultez [Windows Installer des extensions de fichier](https://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Application des règles de Windows Installer  
 Deux ensembles de règles déterminent le déploiement des ressources par le biais des composants de votre installation. Un ensemble de règles est géré par le Windows Installer lui-même, tandis que vous devez appliquer le deuxième jeu en tant qu’auteur d’installation.  
  
> [!NOTE]
> L’application de règles de Windows Installer se produit uniquement si vous exécutez une validation de votre fichier. msi. Toutefois, il est recommandé de traiter ces règles comme des pratiques recommandées. Pour plus d’informations, consultez [validation d’une base de données d’installation](https://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) et [validation de package](https://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Règles appliquées par le programme d’installation  
  
- Tous les fichiers d’un composant donné doivent être installés dans le même répertoire. Inversement, les fichiers installés dans des dossiers distincts doivent appartenir à des composants distincts.  
  
- Il ne peut y avoir qu’un seul chemin de clé par composant. Le chemin d’accès de la clé est simplement un fichier ou une clé de Registre qui représente l’ensemble du composant.  
  
#### <a name="component-provider-responsibilities"></a>Responsabilités du fournisseur de composants  
  
- Les deux ressources qui peuvent être livrées séparément dans les versions ultérieures doivent exister dans des composants distincts. Les ressources doivent être regroupées dans le même composant uniquement lorsque vous êtes certain que ces ressources ne seront jamais expédiées séparément. En fait, il est recommandé que toutes les ressources principales (dll, par exemple) existent toujours dans des WICs distincts. Pour plus d’informations, consultez [définition des composants du programme d’installation](https://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
- Aucune ressource avec version ne doit être livrée dans plus d’un WIC.  
  
## <a name="see-also"></a>Voir aussi  
 [Que se passe-t-il si les règles des composants sont rompues ?](https://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)
