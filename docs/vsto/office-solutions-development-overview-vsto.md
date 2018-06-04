---
title: Présentation du développement de solutions Office (VSTO)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 41fe3ab24b3b70c4cef596caa35c0b4173aaa8fd
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34694028"
---
# <a name="office-solutions-development-overview-vsto"></a>Présentation du développement de solutions Office (VSTO)
  En utilisant Microsoft Office comme partie frontale des solutions, vous pouvez tirer parti des interfaces utilisateur et outils Microsoft Office familiers tels que les fonctionnalités de traitement de texte dans Word, les fonctionnalités d'analyse des données d'Excel et les fonctionnalités de gestion de la messagerie électronique d'Outlook. Vous pouvez développer des solutions dans Visual Studio pour personnaliser des applications Office et ajouter les fonctionnalités spécifiques dont vous avez besoin pour vos processus métier. Par exemple, vous pouvez transformer Word en générateur de contrats qui assemble des contrats à partir de parties préexistantes qui peuvent être modifiables ou non. Avec Excel, vous pouvez créer une feuille de calcul de budget automatisée personnalisée pour différents projets. Vos utilisateurs peuvent aussi mettre des solutions Office hors connexion, ce qui permet de rendre des solutions complexes plus pratiques qu'elles ne le seraient en utilisant une architecture basée sur le Web.  
  
 Cette rubrique fournit une vue d'ensemble des types de solutions Office que vous pouvez créer à l'aide des modèles Visual Studio Tools pour Office (VSTO) disponibles dans les Outils de développement Office dans Visual Studio. Pour obtenir des informations générales sur le développement avec Office, consultez le [Centre pour développeurs Office](https://dev.office.com/).  
  
## <a name="choose-an-office-project-type"></a>Choisissez un type de projet Office  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fournit les types suivants de modèles de projet pour le développement de solutions Office basées sur VSTO :  
  
-   Les**personnalisations au niveau du document** sont associées à un document spécifique.  
  
-   Les**VSTO Add-ins** sont associés à l'application elle-même.  
  
 Pour choisir le type de projet le mieux adapté à votre solution, déterminez si vous souhaitez que votre code s'exécute uniquement quand un document spécifique est ouvert ou si vous souhaitez que le code soit disponible à chaque exécution de l'application. Pour plus d’informations sur les modèles de projet, consultez [vue d’ensemble des modèles de projet Office](../vsto/office-project-templates-overview.md).  
  
 Les types de projets que vous pouvez créer dépendent des applications Office installées sur l'ordinateur de développement. Pour plus d’informations, consultez [fonctionnalités disponibles par type d’application et de projet Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="document-level-customizations"></a>Personnalisations au niveau du document  
 Les personnalisations au niveau du document se composent d'un assembly associé à un document, classeur ou modèle unique dans Microsoft Office Word ou Microsoft Office Excel. L'assembly est chargé quand le document associé est ouvert. Les fonctionnalités des personnalisations que vous créez sont disponibles uniquement quand le document associé est ouvert. Les personnalisations ne peuvent pas apporter de modifications au niveau de l'application, comme l'affichage d'un nouvel élément de menu ou onglet de ruban quand un document est ouvert.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclut des outils pour vous aider à créer des personnalisations au niveau du document. Le document que vous personnalisez est hébergé comme une aire de conception dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], ce qui permet de concevoir le document par glisser-déplacer de contrôles. De nombreuses autres fonctionnalités [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sont disponibles dans les projets au niveau du document, tels que les contrôles Windows Forms, les liaisons de données par glisser-déplacer et un débogueur intégré.  
  
 Pour plus d'informations sur les personnalisations, consultez les rubriques suivantes :  
  
-   [Prise en main de programmation de personnalisations au niveau du document pour Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)  
  
-   [Prise en main de programmation de personnalisations au niveau du document pour Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)  
  
-   [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)  
  
### <a name="vsto-add-ins"></a>Compléments VSTO  
 Les compléments VSTO sont constitués d'un assembly associé à une application Microsoft Office. En général, le complément VSTO est exécuté au démarrage de l’application associée, bien que les utilisateurs puissent également charger des compléments VSTO quand l’application est en cours d’exécution. Les fonctionnalités des compléments VSTO que vous créez sont accessibles à l’application, quels que soient les documents ouverts.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclut des outils pour vous aider à créer des compléments VSTO. Les projets de complément incluent une classe générée automatiquement qui représente le complément VSTO. Cette classe fournit des propriétés et événements que vous pouvez utiliser pour accéder au modèle objet de l’application hôte et exécuter du code quand le complément VSTO est chargé et arrêté. De nombreuses autres fonctionnalités [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] sont disponibles dans les projets de complément VSTO, comme Windows Forms et un débogueur intégré.  
  
 Pour plus d’informations sur les compléments VSTO, consultez les rubriques suivantes :  
  
-   [Prise en main de programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Architecture des compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatiser des applications Office à l’aide d’assemblys PIA  
 Vous pouvez incorporer par programme les fonctionnalités d'une application Office dans votre solution en écrivant du code qui accède au modèle objet de l'application. Les modèles objet sont une organisation de classes qui exposent des fonctionnalités via diverses propriétés et méthodes. Le modèle objet est différent pour chaque application Office.  
  
 Pour utiliser le modèle objet d'une application Office à partir d'une solution créée à l'aide des Outils de développement Office dans [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vous devez utiliser l'assembly PIA pour l'application. L'assembly PIA permet au code managé dans votre solution d'interagir avec le modèle objet COM de l'application Office.  
  
 Pour que vous puissiez effectuer la plupart des tâches de développement, les assemblys PIA d'Office doivent être installés et inscrits dans le Global Assembly Cache de votre ordinateur de développement. Pour plus d’informations, consultez [configurer un ordinateur pour développer des solutions Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Les assemblys PIA d'Office ne sont pas requis sur les ordinateurs des utilisateurs finaux pour l'exécution des solutions Office VSTO. Pour plus d’informations, consultez [conception et créer des solutions Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Pour plus d'informations sur l'utilisation d'assemblys PIA dans les solutions Office VSTO, consultez les rubriques suivantes :  
  
-   [Écrire du code dans les solutions Office](../vsto/writing-code-in-office-solutions.md)  
  
-   [Assemblys PIA Office](../vsto/office-primary-interop-assemblies.md)  
  
## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Exécuter des solutions Office VSTO de Microsoft sur les ordinateurs des utilisateurs finaux  
 Quand vous créez une solution Office VSTO, vous devez réfléchir à la façon dont les spécifications de déploiement peuvent affecter vos choix de développement.  
  
### <a name="deployment-options"></a>Options de déploiement  
 Utilisez ClickOnce ou Windows Installer pour déployer les solutions que vous créez à l'aide des Outils de développement Office de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Le déploiement ClickOnce vous permet de créer des solutions à mise à jour automatique qui peuvent être installées et exécutées avec une intervention minimale de l'utilisateur. Windows Installer (*.msi*) fichiers peuvent être facilement distribués aux ordinateurs des utilisateurs finaux ou distribués à l’aide de Systems Management Server (SMS). Pour plus d’informations sur le déploiement de solutions Office VSTO, consultez [déployer une solution Office](../vsto/deploying-an-office-solution.md).  
  
### <a name="install-prerequisites"></a>Installation des composants requis  
 Avant que les utilisateurs finaux ne puissent exécuter une solution créée à l'aide des Outils de développement Office de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], certains composants doivent être installés sur leur ordinateur. Si vous déployez votre solution en utilisant ClickOnce ou en créant un fichier Windows Installer, ces composants requis peuvent être installés avec votre solution. Pour plus d’informations, consultez [conditions de solution Office pour le déploiement](http://msdn.microsoft.com/en-us/9f672809-43a3-40a1-9057-397ce3b5126e) et [Comment : installer les composants requis sur les ordinateurs des utilisateurs finaux pour exécuter des solutions Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
### <a name="security"></a>Sécurité  
 La sécurité pour les solutions Office VSTO est appliquée par une série de contrôles effectués par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] au moment de l'installation et du chargement de la solution. Ces contrôles permettent notamment de vérifier si l'emplacement du manifeste de déploiement ou le certificat utilisé pour signer le manifeste est approuvé. Pour plus d’informations, consultez [les solutions Office de sécuriser](../vsto/securing-office-solutions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main &#40;développement Office dans Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Architecture des personnalisations au niveau du document](../vsto/architecture-of-document-level-customizations.md)   
 [Architecture des Compléments VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Prise en main de programmation de personnalisations au niveau du document pour Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Prise en main de programmation de personnalisations au niveau du document pour Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Prise en main de programmation de compléments VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  