---
title: Composants requis, boîte de dialogue
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf555a9a4b7c73e4e204bcc42e6b57d3ab96cd01
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419170"
---
# <a name="prerequisites-dialog-box"></a>Composants requis, boîte de dialogue

La boîte de dialogue **Composants requis** spécifie quels composants requis sont installés, comment ils sont installés et l’ordre dans lequel les packages sont installés.

![Boîte de dialogue Composants requis de Visual Studio](media/prerequisites-dialog-box.png)

Pour accéder à la boîte de dialogue, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis sélectionnez **Projet** > **Propriétés**. Quand le **Concepteur de projet** s’affiche, sélectionnez l’onglet **publier**, puis sélectionnez **Composants requis**. Pour les projets d’installation, dans le menu **Projet**, cliquez sur **Propriétés**. Quand la boîte de dialogue **Pages de propriétés** apparaît, cliquez sur **Composants requis**.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

|Élément|Description|
|-------------|-----------------|
|**Créer un programme d’installation des composants requis**|Inclut les composants requis dans le programme d’installation de votre application (*setup.exe*) afin qu’ils soient installés avant votre application, par ordre de dépendance. Cette option est activée par défaut. Si elle n’est pas activée, aucun fichier *Setup.exe* n’est créé.|
|**Choisir les composants requis à installer**|Spécifie s’il faut installer des composants tels que le .NET Framework et les bibliothèques runtime C++.<br /><br />Par exemple, en cochant la case en regard de **SQL Server 2012 Express**, vous indiquez au programme d’installation qu’il doit vérifier si ce composant est installé sur l’ordinateur cible et qu’il doit l’installer si ce n’est déjà fait.<br /><br />Pour plus d’informations sur les packages de composants requis, consultez [Informations sur les composants requis](#prerequisites-information).|
|**Télécharger les composants requis à partir du site web du fournisseur de composants**|Fait en sorte que les composants requis soient installés à partir du site web du fournisseur. Il s'agit de l'option par défaut.|
|**Télécharger les composants requis à partir de l’emplacement de mon application**|Fait en sorte que les composants requis soient installés à partir du même emplacement que l'application. Copie tous les packages de composants requis à l'emplacement de publication. Pour que cette option fonctionne, les packages de composants requis doivent être sur l'ordinateur de développement.|
|**Télécharger les composants requis depuis l’emplacement suivant**|Fait en sorte que les composants requis soient installés à partir de l’emplacement que vous entrez. Vous pouvez utiliser le bouton **Parcourir** pour sélectionner un emplacement.|

> [!NOTE]
> Pour plus d’informations sur l’emplacement des prérequis, consultez [Créer des packages de programme d’amorçage](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages).

## <a name="prerequisites-information"></a>Informations sur les composants requis

Les composants requis qui apparaissent dans la boîte de dialogue **Composants requis** peuvent différer de ceux de la liste suivante. Les packages de prérequis répertoriés dans la **boîte de dialogue Composants requis** sont définis automatiquement la première fois que vous ouvrez la boîte de dialogue. Si vous modifiez ultérieurement le framework cible du projet, vous devrez sélectionner manuellement les composants requis pour qu’ils correspondent à la nouvelle version cible du framework.

|Élément|Description|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Ce package installe les éléments suivants :<br /><br /> - .NET Framework versions 2.0, 3.0 et 3.5.<br />- Prise en charge de toutes les versions de .NET Framework sur les systèmes d’exploitation 32 bits (x86) et 64 bits (x64).<br />- Modules linguistiques pour chaque version de .NET Framework installée avec le package.<br />- Service Packs pour .NET Framework 2.0 et 3.0.<br /><br /> .NET Framework 3.0 est inclus avec Windows Vista et .NET Framework 3.5 avec Visual Studio. .NET Framework 3.5 est requis pour tous les projets Visual Basic et C# qui sont compilés pour les systèmes d’exploitation 32 bits et dont la version cible de .NET Framework est **.NET Framework 3.5**, ainsi que pour les projets Visual Basic et C# compilés pour les systèmes d’exploitation 64 bits. (IA64 n’est pas pris en charge.) Notez que les projets Visual Basic et C# sont compilés pour toute architecture d’UC par défaut. Pour plus d’informations, consultez [Vue d’ensemble du ciblage des frameworks](../../ide/visual-studio-multi-targeting-overview.md) et [Déployer les prérequis pour les applications 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4.x**|Ce package installe .NET Framework 4.x pour les plateformes x64 et x86.|
|**Microsoft System CLR Types pour SQL Server 2014 (x64 et x86)**|Ce package installe Microsoft System CLR Types pour SQL Server 2014 pour les plateformes x64 ou x86.|
|**SQL Server 2008 R2 Express**|Ce package installe Microsoft SQL Server 2008 R2 Express, qui est une version gratuite de Microsoft SQL Server 2008 R2, une base de données idéale pour les petites applications web, de serveur ou de poste de travail. Il peut être utilisé gratuitement pour le développement et la production.|
|**SQL Server 2012 Express**|Ce package installe Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Ce package installe SQL Server 2012 Express LocalDB.|
|**Bibliothèques Runtime Visual C++ "14" (ARM)**|Ce package installe les bibliothèques Runtime Visual C++ pour l'architecture Intel Itanium, qui fournit des routines de programmation pour le système d'exploitation Microsoft Windows. Ces routines automatisent de nombreuses tâches de programmation courantes qui ne sont pas fournies par les langages C et C++.<br /><br /> Pour plus d’informations, consultez [Référence sur les bibliothèques Runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliothèques Runtime Visual C++ "14" (x64)**|Ce package installe les bibliothèques Runtime Visual C++ pour les systèmes d'exploitation x64, qui fournissent des routines de programmation pour le système d'exploitation Microsoft Windows. Ces routines automatisent de nombreuses tâches de programmation courantes qui ne sont pas fournies par les langages C et C++.<br /><br /> Pour plus d’informations, consultez [Référence sur les bibliothèques Runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Bibliothèques Runtime Visual C++ "14" (x86)**|Ce package installe les bibliothèques Runtime Visual C++ pour les systèmes d'exploitation x86, qui fournissent des routines de programmation pour le système d'exploitation Microsoft Windows. Ces routines automatisent de nombreuses tâches de programmation courantes qui ne sont pas fournies par les langages C et C++.<br /><br /> Pour plus d’informations, consultez [Référence sur les bibliothèques Runtime C](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Voir aussi

- [Page Publier, Concepteur de projets](../../ide/reference/publish-page-project-designer.md)
- [Conditions préalables pour le déploiement d’applications](../../deployment/application-deployment-prerequisites.md)
- [Déploiement des prérequis pour les applications 64 bits](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Vue d’ensemble du ciblage des frameworks](../../ide/visual-studio-multi-targeting-overview.md)
