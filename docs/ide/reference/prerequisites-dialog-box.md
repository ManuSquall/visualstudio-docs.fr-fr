---
title: "Composants requis, boîte de dialogue | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Prerequisites dialog box
ms.assetid: 53ac863c-77a0-409b-91e5-7a4bd8b8474e
caps.latest.revision: 75
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: b88c533d613d531a7dcc24e0610e2fb2a7a3d880
ms.lasthandoff: 04/05/2017

---
# <a name="prerequisites-dialog-box"></a>Prerequisites Dialog Box
Cette boîte de dialogue spécifie quels composants requis sont installés, comment ils sont installés et l'ordre dans lequel les packages sont installés.  
  
 Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Lorsque le **Concepteur de projets** apparaît, cliquez sur l'onglet **Publier** . Dans la page **Publier**, cliquez sur le bouton **Composants requis**. Pour les projets d’installation, dans le menu **Projet**, cliquez sur **Propriétés**. Quand la boîte de dialogue **Pages de propriétés** apparaît, cliquez sur **Composants requis**.  
  
## <a name="uielement-list"></a>Liste UIElement  
  
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
|**.NET Framework 3.5 SP1**|Ce package installe les éléments suivants :<br /><br /> - .NET Framework versions 2.0, 3.0 et 3.5.<br />- Prise en charge de toutes les versions de .NET Framework sur les systèmes d’exploitation 32 bits (x86) et 64 bits (x64).<br />- Modules linguistiques pour chaque version de .NET Framework installée avec le package.<br />- Service Packs pour .NET Framework 2.0 et 3.0.<br /><br /> .NET Framework 3.0 est inclus avec Windows Vista et .NET Framework 3.5 avec [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. .NET Framework 3.5 est requis pour tous les projets Visual Basic et Visual C# qui sont compilés pour les systèmes d’exploitation 32 bits et dont la version cible de .NET Framework est **.NET Framework 3.5**, ainsi que pour les projets Visual Basic et Visual C# compilés pour les systèmes d’exploitation 64 bits. (IA64 non pris en charge.) Notez que les projets Visual Basic et Visual C# sont compilés par défaut pour toutes les architectures UC. Pour plus d’informations, consultez [Vue d’ensemble du multiciblage Visual Studio](../../ide/visual-studio-multi-targeting-overview.md), [Redistributing the .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287) (Redistribution du .NET Framework) et [Composants requis pour le déploiement d’applications 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Cet élément est sélectionné par défaut.|  
|**.NET Framework 3.5 SP1 Client Profile**|.NET Framework Client Profile est un sous-ensemble de .NET Framework 3.5 SP1 complet qui cible des applications clientes. Il fournit un sous-ensemble simplifié de fonctionnalités Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) et ClickOnce. Cela permet des scénarios de déploiement rapides pour les applications WPF, Windows Forms, WCF et console qui ciblent .NET Framework Client Profile. Pour plus d’informations, consultez [.NET Framework Client Profile](http://msdn.microsoft.com/Library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Microsoft .NET Framework 4 (x86 et x64)**|Ce package installe .NET Framework 4 pour les plateformes x64 et x86.<br /><br /> Pour plus d’informations, consultez [Vue d’ensemble du multiciblage Visual Studio](../../ide/visual-studio-multi-targeting-overview.md), [Redistributing the .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287) (Redistribution du .NET Framework) et [Composants requis pour le déploiement d’applications 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Cet élément est sélectionné par défaut.|  
|**Microsoft .NET Framework 4 Client Profile (x86 et x64)**|.NET Framework 4 Client Profile est un sous-ensemble de .NET Framework 4 complet qui cible des applications clientes. Il fournit un sous-ensemble simplifié de fonctionnalités Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) et ClickOnce. Cela permet des scénarios de déploiement rapides pour les applications WPF, Windows Forms et console qui ciblent .NET Framework 4 Client Profile. Pour plus d’informations, consultez [.NET Framework Client Profile](http://msdn.microsoft.com/Library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Assemblys PIA (Primary Interop Assembly) Microsoft Office 2007**|Ce package installe les assemblys PIA pour les produits Microsoft Office 2007. Ils permettent au code managé d'interagir avec le modèle d'objet COM d'une application Microsoft Office. Pour plus d’informations, consultez [Assemblys PIA (Primary Interop Assembly) Office](/office-dev/office-dev/office-primary-interop-assemblies).|  
|**Microsoft Visual Basic PowerPacks version 10.0**|Les Power Packs sont des compléments, des contrôles, des composants et des outils destinés à vous aider à développer des applications Visual Basic. Cette version contient le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>, qui vous permet d’imprimer le contenu d’un Windows Form, et la Bibliothèque de compatibilité des imprimantes, qui permet au code Printer Visual Basic 6.0 de s’exécuter sans modification.|  
|**Microsoft Visual F# Runtime for .NET 2.0**|Ce package installe les bibliothèques Runtime Visual F# pour les systèmes d'exploitation x64 et x86, permettant ainsi la prise en charge de la programmation fonctionnelle, mais aussi de la programmation orientée objet et impérative (procédurale) traditionnelle. Ce package doit être installé si l'application ou ses composants sont créés dans Visual F# et .NET Framework 2.0, .NET Framework 3.0 ou .NET Framework 3.5.<br /><br /> Pour plus d’informations, consultez [Informations de référence du langage F#](http://msdn.microsoft.com/Library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Microsoft Visual F# Runtime for .NET 4.0**|Ce package installe les bibliothèques Runtime Visual F# pour les systèmes d'exploitation x64 et x86, permettant ainsi la prise en charge de la programmation fonctionnelle, mais aussi de la programmation orientée objet et impérative (procédurale) traditionnelle. Ce package doit être installé si l'application ou ses composants sont créés dans Visual F# et .NET Framework 4.<br /><br /> Pour plus d’informations, consultez [Informations de référence du langage F#](http://msdn.microsoft.com/Library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Visionneuse de rapports Microsoft Visual Studio 2010**|Ce package installe les contrôles de la visionneuse de rapports que vous pouvez utiliser pour ajouter des rapports de données élaborés à Windows Forms et aux applications ASP.NET.|  
|**Microsoft Visual Studio 2010 for Office Runtime (x86 et x64)**|Les outils de développement Microsoft Office dans Visual Studio offrent des outils intégrés et simples d'utilisation permettant de créer des solutions métier personnalisées avec Microsoft Office. Vous pouvez créer des solutions clientes gérées et intelligentes qui utilisent les applications Office comme une interface utilisateur. Les outils aident les développeurs à créer des solutions sécurisées faciles à déployer et à gérer.<br /><br /> Pour plus d’informations, consultez [Comment : publier une solution Office à l’aide de ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).|  
|**SQL Server 2005 Express Edition SP2 (x86)**|Ce package installe Microsoft SQL Server 2005 Express Edition SP2, une application de base de données basée sur [!INCLUDE[sqprsqext](../../ide/reference/includes/sqprsqext_md.md)]. SQL Server Express remplace Microsoft SQL Server Desktop Engine (MSDE). SQL Server Express est gratuit et peut être redistribué (soumis au contrat). Il fonctionne comme une base de données cliente et comme une base de données serveur de base. Il est identique à SQL Server 2005, à l'exception des éléments suivants :<br /><br /> - Aucune prise en charge des fonctionnalités d’entreprise.<br />- Limité à une UC.<br />- Limite de mémoire de 1 gigaoctet (Go) pour le pool de mémoires tampons.<br />- Taille maximale de 4 Go pour les bases de données.|  
|**SQL Server 2008 Express**|Ce package installe Microsoft SQL Server 2008 Express, une version gratuite de Microsoft SQL Server 2008, une base de données idéale pour les petites applications de bureau, applications serveur ou applications Web. Il peut être utilisé gratuitement pour le développement et la production. Une [inscription](http://go.microsoft.com/fwlink/?LinkId=130380) gratuite est requise pour distribuer SQL Server 2008 Express avec l’application.<br /><br /> Le comportement du programme d'amorçage est le suivant :<br /><br /> - Si l’ordinateur dispose déjà de SQL Server 2008 Express ou version ultérieure, il le conserve.<br />- Si l’ordinateur ne dispose d’aucune version de SQL Server 2008 Express ou version ultérieure, le package installe la dernière version de SQL Server 2008 Express SP1.<br /><br /> Pour en savoir plus sur SQL Server 2008 Express, visitez [http://go.microsoft.com/fwlink/?LinkId=183586](http://go.microsoft.com/fwlink/?LinkId=183586).|  
|**Bibliothèques Runtime Visual C++ 2010 (IA64)**|Ce package installe les bibliothèques Runtime Visual C++ pour l'architecture Intel Itanium, qui fournit des routines de programmation pour le système d'exploitation Microsoft Windows. Ces routines automatisent de nombreuses tâches de programmation courantes qui ne sont pas fournies par les langages C et C++.<br /><br /> Pour plus d’informations, consultez [Référence sur les bibliothèques Runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|  
|**Bibliothèques Runtime Visual C++ 2010 (x64)**|Ce package installe les bibliothèques Runtime Visual C++ pour les systèmes d'exploitation x64, qui fournissent des routines de programmation pour le système d'exploitation Microsoft Windows. Ces routines automatisent de nombreuses tâches de programmation courantes qui ne sont pas fournies par les langages C et C++.<br /><br /> Pour plus d’informations, consultez [Référence sur les bibliothèques Runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|  
|**Bibliothèques Runtime Visual C++ 2010 (x86)**|Ce package installe les bibliothèques Runtime Visual C++ pour les systèmes d'exploitation x86, qui fournissent des routines de programmation pour le système d'exploitation Microsoft Windows. Ces routines automatisent de nombreuses tâches de programmation courantes qui ne sont pas fournies par les langages C et C++.<br /><br /> Pour plus d’informations, consultez [Référence sur les bibliothèques Runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|  
|**Windows Installer 3.1**|Ce package installe la version 3.1 du redistribuable Microsoft Windows Installer, qui permet l'installation de projets d'installation Windows Installer. Il est préinstallé sur Windows Server 2003 avec SP1 et versions ultérieures.<br /><br /> Cet élément est sélectionné par défaut.|  
|**Windows Installer 4.5**|Ce package installe la version 4.5 du redistribuable Microsoft Windows Installer, qui permet l’installation de projets d’installation Windows Installer.|  
  
## <a name="see-also"></a>Voir aussi  
 [Page Publier, Concepteur de projets](../../ide/reference/publish-page-project-designer.md)   
 [Prérequis pour le déploiement d’applications](../../deployment/application-deployment-prerequisites.md)   
 [Redistribution du .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287)   
 [Déploiement des prérequis pour les applications 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md)   
 [Vue d’ensemble du multiciblage Visual Studio](../../ide/visual-studio-multi-targeting-overview.md)
