---
title: Architecture des personnalisations au niveau du document
description: Découvrez les aspects des personnalisations au niveau du document, y compris les composants de personnalisation et le fonctionnement des personnalisations avec les applications Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a101fa597764538c0a1c09e7b4e5de2c81606346
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948724"
---
# <a name="architecture-of-document-level-customizations"></a>Architecture des personnalisations au niveau du document
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] comprend des projets pour créer des personnalisations au niveau du document pour Microsoft Office Word et Microsoft Office Excel. Cette rubrique décrit les aspects suivants des personnalisations au niveau du document :

- [Présentation des personnalisations](#UnderstandingCustomizations)

- [Composants des personnalisations](#Components)

- [Fonctionnement des personnalisations avec les applications Microsoft Office](#HowCustomizationsWork)

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Pour obtenir des informations générales sur la création de personnalisations au niveau du document, consultez [vue d’ensemble du développement des solutions Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md), [prise en main de la programmation des personnalisations au niveau du document pour Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)et [prise en main de la programmation des personnalisations au niveau du document pour Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md).

## <a name="understand-customizations"></a><a name="UnderstandingCustomizations"></a> Présentation des personnalisations
 Quand vous utilisez les Outils de développement Office dans Visual Studio pour générer une personnalisation au niveau du document, vous créez un assembly de code managé associé à un document spécifique. On dit d’un document ou classeur lié à un assembly qu’il a des extensions de code managé. Pour plus d’informations, consultez [conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md).

 Quand un utilisateur ouvre le document, l’assembly est chargé par l’application Microsoft Office. Une fois l’assembly chargé, la personnalisation peut répondre à des événements pendant que le document est ouvert. La personnalisation peut également exécuter un appel dans le modèle objet pour automatiser et étendre l’application pendant que le document est ouvert, et elle peut utiliser toutes les classes du [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].

 L'assembly communique avec les composants COM de l'application à travers l'assembly PIA (Primary Interop Assembly) de celle-ci. Pour plus d’informations, consultez [assemblys PIA (Primary Interop Assembly) Office](../vsto/office-primary-interop-assemblies.md) et [vue d’ensemble du développement de solutions office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 Si un utilisateur ouvre plusieurs personnalisations au niveau du document en même temps, chaque assembly est chargé dans un domaine d’application différent. Cela signifie qu’une solution dont le comportement est incorrect ne peut pas entraîner l’échec d’autres solutions. Les personnalisations au niveau du document sont conçues pour fonctionner avec un seul document dans un seul domaine d’application. Elles ne sont pas conçues pour la communication entre documents. Pour plus d’informations sur les domaines d’application, consultez [domaines d’application](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> Les personnalisations au niveau du document que vous créez à l’aide des Outils de développement Office dans Visual Studio sont conçues pour être utilisées seulement quand l’application est démarrée par un utilisateur final. Si elle est démarrée par programmation (par exemple à l’aide d’Automation), la personnalisation risque de ne pas fonctionner correctement.

### <a name="design-time-and-run-time-experiences"></a>Expériences au moment du design et au moment de l’exécution
 Pour comprendre l’architecture des personnalisations au niveau du document, il est utile de comprendre les expériences de conception et d’exécution d’une solution.

#### <a name="design-time"></a>Au moment du design
 L’expérience au moment du design comprend les étapes suivantes :

1. Le développeur crée un projet au niveau du document dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Le projet comprend le document et l’assembly qui s’exécute derrière le document. Le document peut déjà exister (créé par un concepteur) ou un nouveau document peut être créé en même temps que le projet.

2. Le concepteur (le développeur qui crée le projet ou une autre personne) crée l’apparence finale du document pour l’utilisateur final.

#### <a name="runtime"></a>Runtime
 L’expérience au moment de l’exécution comprend les étapes suivantes :

1. L’utilisateur final ouvre un document ou un classeur qui a des extensions de code managé.

2. Le document ou le classeur charge l’assembly compilé.

3. L’assembly répond aux événements à mesure que l’utilisateur travaille dans le document ou le classeur.

#### <a name="developer-and-end-user-perspective-compared"></a>Comparaison du point de vue du développeur et de l’utilisateur final
 Étant donné que le développeur travaille principalement dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]et l’utilisateur final dans Word ou Excel, il existe deux façons de comprendre les personnalisations au niveau du document.

|Perspective du développeur|Perspective de l’utilisateur final|
|-----------------------------|----------------------------|
|À l’aide de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le développeur écrit du code accessible à Word et Excel.<br /><br /> Bien qu’il puisse sembler que le développeur crée un fichier exécutable qui exécute Word ou Excel, c’est en fait le processus inverse qui se produit. Le document est associé à un assembly et contient un pointeur vers cet assembly. Quand le document s’ouvre, Word ou Excel recherche l’assembly et exécute le code en réponse à tous les événements gérés.|Ceux qui utilisent la solution ouvrent simplement le document ou le classeur (ou créent un document à partir d’un modèle), comme ils le feraient pour n’importe quel autre fichier Microsoft Office.<br /><br /> L’assembly fournit des personnalisations dans le document ou le classeur, telles que le remplissage automatique avec des données à jour ou l’affichage d’une boîte de dialogue pour demander des informations.|

### <a name="supported-document-formats-for-document-level-customizations"></a>Formats de document pris en charge pour les personnalisations au niveau du document
 Quand vous créez un projet de personnalisation, vous pouvez choisir le format du document que vous souhaitez utiliser dans le projet. Pour plus d’informations, consultez [Comment : créer des projets Office dans Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Le tableau suivant répertorie les formats de documents que vous pouvez utiliser dans les personnalisations au niveau du document pour Excel et Word.

|Excel|Word|
|-----------|----------|
|Classeur Excel (*. xlsx*)<br /><br /> Classeur Excel prenant en charge les macros (*. xlsm*)<br /><br /> Classeur binaire Excel (*. xlsb*)<br /><br /> Classeur Excel 97-2003 (*. xls*)<br /><br /> Modèle Excel (*. xltx*)<br /><br /> Modèle Excel prenant en charge les macros (*. xltm*)<br /><br /> Modèle Excel 97-2003 (*. xlt*)|Document Word (*. docx*)<br /><br /> Document Word prenant en charge les macros (*. docm*)<br /><br /> Document Word 97-2003 (*. doc*)<br /><br /> Modèle Word (*. dotx*)<br /><br /> Modèle Word prenant en charge les macros (*. dotm*)<br /><br /> Modèle Word 97-2003 (*. dot*)|

 Vous devez concevoir des extensions de code managé uniquement pour les documents dont le format est pris en charge. Sinon, certains événements risquent de ne pas être déclenchés lorsque le document s’ouvre dans l’application. Par exemple, l' <xref:Microsoft.Office.Tools.Excel.Workbook.Open> événement n’est pas déclenché quand vous utilisez des extensions de code managé avec des classeurs enregistrés au format feuille de calcul XML Excel ou dans la page Web (*. htm*; *. html*) format.

### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Prise en charge des documents Word ayant des extensions de nom de fichier. Xml
 Les modèles de projets au niveau du document ne vous permettent pas de créer des projets basés sur les formats de fichiers suivants :

- Document XML Word (*\* XML*).

- Document XML Word 2003 (*\* XML*).

  Si vous souhaitez que vos utilisateurs finaux utilisent des personnalisations dans ces formats de fichiers, générez et déployez une personnalisation qui utilise l’un des formats de fichiers pris en charge spécifiés dans le tableau ci-dessus. Après l’installation de la personnalisation, les utilisateurs finaux peuvent enregistrer le document au format document XML Word (*\* XML*) ou au format document XML Word 2003 (*\* XML*), et la personnalisation continue à fonctionner comme prévu.

## <a name="components-of-customizations"></a><a name="Components"></a> Composants des personnalisations
 Les principaux composants d’une personnalisation sont le document et l’assembly. Outre ces composants, il en existe plusieurs autres qui jouent un rôle important dans la manière dont les applications Microsoft Office découvrent et chargent les personnalisations.

### <a name="deployment-manifest-and-application-manifest"></a>Manifeste de déploiement et manifeste d’application
 Les personnalisations utilisent des manifestes de déploiement et des manifestes d’application pour identifier et charger la version la plus récente de l’assembly de personnalisation. Le manifeste de déploiement pointe vers le manifeste d'application actuel. Le manifeste d’application pointe vers l’assembly de personnalisation et spécifie la ou les classes de point d’entrée à exécuter dans l’assembly. Pour plus d’informations, consultez [manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

### <a name="visual-studio-tools-for-office-runtime"></a>Visual Studio Tools pour Office Runtime
 Pour exécuter des personnalisations au niveau du document créées à l’aide des outils de développement Office dans Visual Studio, le doit être installé sur les ordinateurs des utilisateurs finaux [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] comprend des composants non managés qui chargent l’assembly de personnalisation, ainsi qu’un jeu d’assemblys managés. Ces assemblys managés fournissent le modèle objet utilisé par votre code de personnalisation pour automatiser et étendre l’application hôte.

 Pour plus d’informations, consultez [vue d’ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-customizations-work-with-microsoft-office-applications"></a><a name="HowCustomizationsWork"></a> Fonctionnement des personnalisations avec les applications Microsoft Office
 Quand un utilisateur ouvre un document qui fait partie d’une personnalisation Microsoft Office, l’application utilise le manifeste de déploiement lié au document pour rechercher et charger la version la plus récente de l’assembly de personnalisation. L’emplacement du manifeste de déploiement est stocké dans une propriété de document personnalisée nommée **AssemblyLocation**. La chaîne qui identifie cet emplacement est insérée dans la propriété lorsque vous générez la solution.

 Le manifeste de déploiement pointe vers le manifeste d’application, qui pointe vers l’assembly le plus récent. Pour plus d’informations, consultez [manifestes d’application et de déploiement dans les solutions Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 L’illustration suivante montre l’architecture de base d’une personnalisation au niveau du document.

 ![Architecture de personnalisation d'Office 2007](../vsto/media/office07-custom.png "Architecture de personnalisation d'Office 2007")

> [!NOTE]
> Dans les solutions Office qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], les solutions exécutent un appel dans le modèle objet de l’application hôte à l’aide des informations de type d’assembly PIA incorporées dans l’assembly de solution, au lieu d’exécuter un appel directement dans l’assembly PIA. Pour plus d’informations, consultez [conception et création de solutions Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Chargement du processus
 Les étapes suivantes se produisent lorsqu’un utilisateur ouvre un document qui fait partie d’une solution Microsoft Office.

1. L’application Microsoft Office vérifie les propriétés de document personnalisées pour voir si des extensions de code managé sont associées au document. Pour plus d’informations, consultez [vue d’ensemble des propriétés de document personnalisé](../vsto/custom-document-properties-overview.md).

2. S’il existe des extensions de code managé, l’application charge *VSTOEE.dll*, qui charge *VSTOLoader.dll*. Il s’agit de dll non managées qui sont les composants du chargeur pour Visual Studio 2010 Tools pour Office Runtime. Pour plus d’informations, consultez [vue d’ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader.dll* charge le [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] et démarre la partie managée de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

4. Si le document est ouvert à partir d’un emplacement autre que l’ordinateur local, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vérifie que l’emplacement du document figure dans la liste **Emplacements approuvés** dans les **Paramètres du Centre de gestion de la confidentialité** pour cette application Office. Si l’emplacement du document n’est pas un emplacement approuvé, la personnalisation n’est pas approuvée et le processus de chargement est arrêté.

5. Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] installe la solution si ce n’est déjà fait, télécharge les manifestes de déploiement et d’application les plus récents, et exécute une série de vérifications de sécurité. Pour plus d’informations, consultez [sécuriser les solutions Office](../vsto/securing-office-solutions.md).

6. Si l’exécution de la personnalisation est approuvée, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] utilise le manifeste de déploiement et le manifeste d’application pour rechercher des mises à jour de l’assembly. Si une nouvelle version de l'assembly est disponible, le runtime la télécharge dans le cache de [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] sur l'ordinateur client. Pour plus d’informations, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).

7. Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] crée un domaine d’application dans lequel charger l’assembly de la personnalisation.

8. Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] charge l’assembly de la personnalisation dans le domaine d’application.

9. Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] appelle le gestionnaire d’événements **Startup** dans votre assembly de personnalisation. Pour plus d’informations, consultez [événements dans les projets Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Voir aussi
- [Architecture des solutions Office dans Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Vue d’ensemble de Visual Studio Tools pour Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Sécuriser les solutions Office](../vsto/securing-office-solutions.md)
- [Concevoir et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md)
- [Vue d’ensemble des propriétés de document personnalisées](../vsto/custom-document-properties-overview.md)
- [Données mises en cache dans les personnalisations au niveau du document](../vsto/cached-data-in-document-level-customizations.md)
