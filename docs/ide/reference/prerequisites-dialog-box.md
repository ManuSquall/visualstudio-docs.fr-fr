---
title: "Composants requis, boîte de dialogue | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3d97e1f37c1e60c3ec5bb122a6b3f26c2fb086f9
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="prerequisites-dialog-box"></a>Prerequisites Dialog Box

Cette boîte de dialogue spécifie quels composants requis sont installés, comment ils sont installés et l'ordre dans lequel les packages sont installés.

Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Lorsque le **Concepteur de projets** apparaît, cliquez sur l'onglet **Publier** . Dans la page **Publier**, cliquez sur le bouton **Composants requis**. Pour les projets d’installation, dans le menu **Projet**, cliquez sur **Propriétés**. Quand la boîte de dialogue **Pages de propriétés** apparaît, cliquez sur **Composants requis**.

## <a name="uielement-list"></a>Liste des éléments d’interface

|Élément|Description|
|-------------|-----------------|
|**Créer un programme d’installation des composants requis**|Inclut les composants requis dans le programme d'installation de votre application (setup.exe) afin qu'ils soient installés avant votre application, par ordre de dépendance. Cette option est activée par défaut. Si elle n'est pas activée, aucun fichier Setup.exe n'est créé.|
|**Choisir les composants requis à installer**|Spécifie s'il faut installer des composants tels que [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], Crystal Reports, et ainsi de suite.<br /><br /> Par exemple, en cochant la case en regard de **SQL Server 2005 Express Edition SP2**, vous indiquez au programme d’installation qu’il doit vérifier si ce composant est installé sur l’ordinateur cible et l’installer si ce n’est pas déjà fait.<br /><br /> Pour plus d'informations sur les packages de composants requis, consultez le tableau Informations sur les composants requis plus loin dans cette rubrique.|
|**Rechercher d’autres composants redistribuables sur Microsoft Update**|Le fait de cliquer sur ce lien vous renvoie au site web [Packages d’amorçage pour redistribuer des composants](http://go.microsoft.com/fwlink/?LinkId=208835) pour vérifier les mises à jour disponibles.|
|**Télécharger les composants requis à partir du site web du fournisseur de composants**|Fait en sorte que les composants requis soient installés à partir du site web du fournisseur. Il s'agit de l'option par défaut.|
|**Télécharger les composants requis à partir de l’emplacement de mon application**|Fait en sorte que les composants requis soient installés à partir du même emplacement que l'application. Copie tous les packages de composants requis à l'emplacement de publication. Pour que cette option fonctionne, les packages de composants requis doivent être sur l'ordinateur de développement.|
|**Télécharger les composants requis depuis l’emplacement suivant**|Fait en sorte que les composants requis soient installés à partir de l'emplacement que vous sélectionnez. Vous pouvez utiliser le bouton **Parcourir** pour sélectionner un emplacement.|

## <a name="prerequisites-information"></a>Informations sur les composants requis

Les composants requis qui apparaissent dans la boîte de dialogue **Composants requis** peuvent différer de ceux de la liste suivante. Les packages de prérequis répertoriés dans la **boîte de dialogue Composants requis** sont définis automatiquement la première fois que vous ouvrez la boîte de dialogue. Si vous modifiez ultérieurement le framework cible du projet, vous devrez sélectionner manuellement les composants requis pour qu'ils correspondent au nouveau framework cible.

|Élément|Description|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Ce package installe les éléments suivants :<br /><br /> - .NET Framework versions 2.0, 3.0 et 3.5.<br />- Prise en charge de toutes les versions de .NET Framework sur les systèmes d’exploitation 32 bits (x86) et 64 bits (x64).<br />- Modules linguistiques pour chaque version de .NET Framework installée avec le package.<br />- Service Packs pour .NET Framework 2.0 et 3.0.<br /><br /> .NET Framework 3.0 est inclus avec Windows Vista et .NET Framework 3.5 avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. .NET Framework 3.5 est requis pour tous les projets Visual Basic et C# qui sont compilés pour les systèmes d’exploitation 32 bits et dont la version cible de .NET Framework est **.NET Framework 3.5**, ainsi que pour les projets Visual Basic et C# compilés pour les systèmes d’exploitation 64 bits. (IA64 non pris en charge.) Notez que les projets Visual Basic et C# sont compilés par défaut pour toutes les architectures UC. Pour plus d’informations, consultez [Vue d’ensemble du multiciblage Visual Studio](../../ide/visual-studio-multi-targeting-overview.md) et [Composants requis pour le déploiement d’applications 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Cet élément est sélectionné par défaut.|
|**Microsoft .NET Framework 4.x**|Ce package installe .NET Framework 4.x pour les plateformes x64 et x86.|
|**Microsoft System CLR Types pour SQL Server 2014 (x64 et x86)**|Ce package installe Microsoft System CLR Types pour SQL Server 2014 pour les plateformes x64 ou x86.|
|**SQL Server 2008 R2 Express**|Ce package installe Microsoft SQL Server 2008 R2 Express, une version gratuite de Microsoft SQL Server 2008 R2, une base de données idéale pour les petites applications de bureau, applications serveur ou applications Web. Il peut être utilisé gratuitement pour le développement et la production. Une [inscription](http://go.microsoft.com/fwlink/?LinkId=130380) gratuite est requise pour distribuer SQL Server 2008 R2 Express avec l’application.|
|**SQL Server 2012 Express**|Ce package installe Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Ce package installe SQL Server 2012 Express LocalDB.|
|**Bibliothèques Runtime Visual C++ "14" (ARM)**|Ce package installe les bibliothèques Runtime Visual C++ pour l'architecture Intel Itanium, qui fournit des routines de programmation pour le système d'exploitation Microsoft Windows. Ces routines automatisent de nombreuses tâches de programmation courantes qui ne sont pas fournies par les langages C et C++.<br /><br /> Pour plus d’informations, consultez [Référence sur les bibliothèques Runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliothèques Runtime Visual C++ "14" (x64)**|Ce package installe les bibliothèques Runtime Visual C++ pour les systèmes d'exploitation x64, qui fournissent des routines de programmation pour le système d'exploitation Microsoft Windows. Ces routines automatisent de nombreuses tâches de programmation courantes qui ne sont pas fournies par les langages C et C++.<br /><br /> Pour plus d’informations, consultez [Référence sur les bibliothèques Runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliothèques Runtime Visual C++ "14" (x86)**|Ce package installe les bibliothèques Runtime Visual C++ pour les systèmes d'exploitation x86, qui fournissent des routines de programmation pour le système d'exploitation Microsoft Windows. Ces routines automatisent de nombreuses tâches de programmation courantes qui ne sont pas fournies par les langages C et C++.<br /><br /> Pour plus d’informations, consultez [Référence sur les bibliothèques Runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Voir aussi

[Page Publier, Concepteur de projets](../../ide/reference/publish-page-project-designer.md)  
[Prérequis pour le déploiement d’applications](../../deployment/application-deployment-prerequisites.md)  
[Déploiement des prérequis pour les applications 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md)  
[Vue d’ensemble du multiciblage Visual Studio](../../ide/visual-studio-multi-targeting-overview.md)
