---
title: Vue d’ensemble de Visual Studio Tools pour Office Runtime
description: Visual Studio 2010 Tools pour Office Runtime doit être installé sur les ordinateurs des utilisateurs finaux pour exécuter des solutions créées à l’aide des outils de développement Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio], about Office runtime
- VSTOLoader.dll
- runtime loader [Office development in Visual Studio]
- Office runtime [Office development in Visual Studio], assemblies
- Office runtime [Office development in Visual Studio]
- runtime [Office development in Visual Studio], assemblies
- vstoee.dll
- Visual Studio Tools for Office runtime
- Office solutions [Office development in Visual Studio], runtime
- solutions [Office development in Visual Studio], runtime
- versions [Office development in Visual Studio], runtime
- assemblies [Office development in Visual Studio], runtime
- runtime [Office development in Visual Studio], about VSTO runtime
- solution loader [Office development in Visual Studio]
- runtime [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16431a9ba2fe56b88f9f6b7f2c874c75bfad61c3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526277"
---
# <a name="visual-studio-tools-for-office-runtime-overview"></a>Vue d’ensemble de Visual Studio Tools pour Office Runtime
  Pour exécuter des solutions créées à l’aide des outils de développement Microsoft Office dans Visual Studio, Visual Studio 2010 Tools pour Office Runtime doit être installé sur les ordinateurs des utilisateurs finaux. Pour plus d’informations, consultez [Comment : installer le Visual Studio Tools pour le package redistribuable Office Runtime](../vsto/how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md). Visual Studio 2010 Tools pour Office Runtime se compose de deux composants principaux :

- Extensions Office pour .NET Framework. Ces composants sont des assemblys managés qui fournissent la couche de communication entre votre solution et l'application Microsoft Office. Pour plus d’informations, consultez [comprendre les extensions Office pour le .NET Framework](#officeextensions).

- Chargeur de solution Office. Ce composant est un ensemble de DLL non managées que les applications Office utilisent pour charger le runtime et vos solutions. Pour plus d’informations, consultez [comprendre le chargeur de solution Office](#UnmanagedLoader).

  Le runtime peut être installé de plusieurs façons différentes. Selon la configuration de l'ordinateur, différents composants runtime sont installés lorsque vous installez le runtime. Pour plus d’informations, consultez [Visual Studio Tools pour les scénarios d’installation d’Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

## <a name="understand-the-office-extensions-for-the-net-framework"></a><a name="officeextensions"></a> Comprendre les extensions Office pour le .NET Framework
 Visual Studio 2010 Tools pour Office Runtime comprend des extensions Office pour les .NET Framework 3,5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et versions ultérieures. Les solutions qui ciblent chaque version du .NET Framework, utilisent les extensions appropriées pour cette version.

 Ces extensions se composent des assemblys que vos solutions utilisent pour automatiser et étendre des applications Office. Lorsque vous créez un projet Office, Visual Studio ajoute automatiquement des références aux assemblys utilisés pour le type de projet et la version .NET Framework cible du projet. Pour plus d’informations sur les assemblys dans les extensions Office, consultez [assemblys dans le Visual Studio Tools pour Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md).

### <a name="design-differences-in-the-office-extensions"></a>Différences de conception dans les extensions Office
 La plupart des types que vous utilisez dans les extensions Office pour .NET Framework 3.5 sont des classes. Ce sont les mêmes classes que celles fournies dans les versions antérieures de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. En revanche, la plupart des types que vous utilisez dans les extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure sont des interfaces. Par exemple, quand vous ciblez le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, les types <xref:Microsoft.Office.Tools.Excel.Worksheet> et <xref:Microsoft.Office.Tools.Word.Document> sont des interfaces, et non des classes.

 Dans la plupart des cas, le code que vous écrivez dans les solutions Office est le même que votre solution cible .NET Framework 3.5 ou [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Toutefois, certaines fonctionnalités requièrent un code différent lorsque vous ciblez des versions différentes du .NET Framework. Pour plus d’informations, consultez [migrer des solutions Office vers le .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md).

### <a name="interfaces-in-the-office-extensions-for-the-net-framework-4-or-later"></a>Interfaces dans les extensions Office pour le .NET Framework 4 ou version ultérieure
 La plupart des interfaces dans les extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure ne sont pas destinées à être implémentées par du code utilisateur. Les seules interfaces que vous pouvez directement implémenter ont des noms qui commencent par la lettre **I**, tels que <xref:Microsoft.Office.Tools.Excel.ISmartTagExtension>.

 Toutes les interfaces qui ne commencent pas par la lettre **I** sont implémentées en interne par Visual Studio 2010 Tools pour Office Runtime, et ces interfaces peuvent changer dans les versions ultérieures. Pour créer des objets qui implémentent ces interfaces, utilisez les méthodes fournies par l'objet `Globals.Factory` dans votre projet. Par exemple, pour obtenir un objet qui implémente l'interface <xref:Microsoft.Office.Tools.Excel.SmartTag>, utilisez la méthode `Globals.Factory.CreateSmartTag`. Pour plus d’informations sur `Globals.Factory` , consultez [accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="enable-type-equivalence-and-embedded-types-in-projects-that-target-the-net-framework-4-or-later"></a>Activer l’équivalence de type et les types incorporés dans les projets qui ciblent le .NET Framework 4 ou version ultérieure
 Le modèle d'objet des extensions Office pour le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure étant basé sur des interfaces, vous pouvez utiliser la fonctionnalité d'équivalence des types dans Visual C# et Visual Basic dans Visual Studio pour incorporer les informations de type de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dans votre solution. Cette fonctionnalité permet aux solutions Office et à [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] d'être gérés indépendamment les uns des autres. Par exemple, si votre solution utilise l'interface <xref:Microsoft.Office.Tools.Word.Document> comme un type incorporé et que la version suivante du runtime ajoute des membres à l'interface <xref:Microsoft.Office.Tools.Word.Document> , votre solution fonctionnera encore avec la version suivante du runtime. Si votre solution n'utilise pas l'interface <xref:Microsoft.Office.Tools.Word.Document> comme un type incorporé, votre solution ne fonctionnera plus avec la version suivante du runtime.

 Par défaut, la fonctionnalité d'équivalence des types n'est pas activée quand vous créez un projet Office qui cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Si vous souhaitez activer cette fonction, affectez à la propriété **Incorporer les types interop** de chacune des références d'assembly suivantes dans votre projet la valeur **True**:

- Microsoft.Office.Tools.dll

- Microsoft.Office.Tools.Common.dll

- Microsoft.Office.Tools.Excel.dll

- Microsoft.Office.Tools.Outlook.dll

- Microsoft.Office.Tools.Word.dll

  Une fois que vous avez apporté cette modification, les informations de type pour tous les types au moment de l'exécution utilisés par le projet sont incorporées dans l'assembly de solution lorsque vous générez le projet. Ces informations de type incorporées, plutôt que les informations de type dans les assemblys référencés, sont utilisées par la solution au moment de l'exécution.

## <a name="understand-the-office-solution-loader"></a><a name="UnmanagedLoader"></a> Comprendre le chargeur de solution Office
 Le runtime Visual Studio Tools pour Office inclut plusieurs DLL non managées que les applications Office utilisent pour charger le runtime et les solutions Office. Bien que vous ne devriez jamais avoir à utiliser directement ces DLL, le fait de savoir à quoi elles servent peut vous aider à mieux comprendre l'architecture des solutions Office.

 Pour plus d’informations sur la façon dont ces composants sont utilisés pendant le processus de chargement, consultez [architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md) et [architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="vstoeedll"></a>vstoee.dll
 Quand un utilisateur ouvre une personnalisation au niveau du document ou démarre un complément VSTO, l’application Office appelle dans *VSTOEE.dll* pour effectuer les tâches requises pour charger le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 *VSTOEE.dll* s’assurer que la version correcte du [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] est chargée pour la solution et la version installée d’Office. Bien que plusieurs versions de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] puissent être installées sur le même ordinateur, une seule instance de *VSTOEE.dll* est installée à la fois. Il s’agit de l' *VSTOEE.dll* qui a été inclus avec la dernière version du runtime installée sur l’ordinateur. Pour plus d’informations sur les différentes versions de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] qui peuvent être utilisées pour d’autres solutions, consultez [exécuter des solutions dans différentes versions de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

### <a name="vstoloaderdll"></a>VSTOLoader.dll
 Une fois que *VSTOEE.dll* chargé la version appropriée du [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , *VSTOLoader.dll* effectue la majeure partie du travail requis pour charger l’assembly de la solution. *VSTOLoader.dll* effectue plusieurs opérations :

- Il crée un domaine d'application pour chaque assembly de solution.

- Il exécute un ensemble de vérifications de sécurité pour s'assurer que l'exécution de l'assembly de la solution est autorisée.

- Il charge la version des extensions Office pour la version .NET Framework requise par la solution.

  *VSTOLoader.dll* effectue également plusieurs tâches spécifiques aux compléments VSTO :

- Implémente l'interface <xref:Extensibility.IDTExtensibility2> . <xref:Extensibility.IDTExtensibility2> est une interface COM que tous les compléments VSTO pour les applications Microsoft Office doivent implémenter. Cette interface définit les méthodes que l’application appelle pour communiquer avec le complément VSTO.

- Il implémente l’interface IManagedAddin. Cette interface est utilisée par les applications Office pour charger les compléments VSTO. Pour plus d’informations, consultez [IManagedAddin interface](../vsto/imanagedaddin-interface.md).

## <a name="understand-the-32-bit-and-64-bit-versions-of-the-runtime"></a>Présentation des versions 32 bits et 64 bits du Runtime
 Il existe des versions 64 bits et 32 bits distinctes de Visual Studio 2010 Tools pour Office Runtime. Ces versions du runtime sont utilisées pour exécuter des solutions dans les éditions 64 bits et 32 bits d'Office. Le tableau suivant affiche la version requise du runtime pour chaque combinaison de Windows et d'Office.

|Édition de Windows|Édition de Microsoft Office|Version obligatoire du runtime de Visual Studio Tools pour Office.|
|------------------------|---------------------------------|--------------------------------------------------------------------|
|32 bits|32 bits|32 bits|
|64 bits|32 bits|64 bits|
|64 bits|64 bits|64 bits|

 Quand vous installez Office, la version requise de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] est installée avec Office. Par exemple, quand vous installez l'édition 64 bits d'Office sur une version 64 bits de Windows, la version 64 bits de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] est également installée. Pour plus d’informations sur l’installation de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] avec Office, consultez [Visual Studio Tools pour les scénarios d’installation d’Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

 La version 64 bits d'Office peut également exécuter des solutions Office créées à l'aide de modèles de projet pour la version 2007 de Microsoft Office System dans Visual Studio 2008. Toutefois, il ne peut pas exécuter des solutions Office créées en utilisant des modèles de projet pour Microsoft Office 2003 dans Visual Studio 2008, ou des solutions Office créées à l'aide de Visual Studio 2005. Pour plus d’informations, consultez [exécuter des solutions dans différentes versions de Microsoft Office](../vsto/running-solutions-in-different-versions-of-microsoft-office.md).

## <a name="repair-the-visual-studio-2010-tools-for-office-runtime"></a>Réparer Visual Studio 2010 Tools pour Office Runtime
 Si vous devez réparer le runtime, ouvrez **Programmes et fonctionnalités** ou **Ajout/Suppression de programmes** dans le Panneau de configuration, sélectionnez **Microsoft Visual Studio 2010 Tools pour Office Runtime** dans la liste des programmes, puis cliquez sur **Désinstaller**. Le programme d'installation qui s'exécute vous permet de réparer le runtime. Si vous cliquez sur **Modifier**, vous n'aurez pas la possibilité de réparer le runtime.

## <a name="see-also"></a>Voir aussi
- [Visual Studio Tools pour les scénarios d’installation d’Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)
- [Assemblys dans le Visual Studio Tools pour Office Runtime](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)
- [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Mettre à niveau et migrer des solutions Office](../vsto/upgrading-and-migrating-office-solutions.md)
