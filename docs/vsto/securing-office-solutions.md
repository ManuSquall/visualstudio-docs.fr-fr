---
title: "Sécurisation des Solutions Office | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
ms.assetid: af840916-dda4-4e52-b536-802ebcab30ca
caps.latest.revision: "78"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 45052deff58e992b427f72188fcb0dc8ade91b95
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="securing-office-solutions"></a>Sécurisation des solutions Office
  Le modèle de sécurité pour les solutions Office implique plusieurs technologies : le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)], le centre de confidentialité de Microsoft Office et la zone sites sensibles d’Internet Explorer. Les sections suivantes décrivent le fonctionnement de ces différentes fonctionnalités de sécurité :  
  
-   [Octroi de niveaux de confiance à des solutions Office](#GrantingTrustToSolutions)  
  
-   [Accorder la confiance à des Documents](#GrantingTrustToDocuments)  
  
-   [Octroi d’approbation lors de l’utilisation de Windows Installer](#GrantingTrustWindowsInstaller)  
  
-   [Considérations spécifiques sur la sécurité pour les solutions Office](#Security)  
  
-   [Sécurité pendant le développement](#SecurityDuringDeployment)  
  
-   [Visual Studio Tools pour Office Runtime](#VisualStudioToolsForOfficeRuntime)  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
##  <a name="GrantingTrustToSolutions"></a>Accorder la confiance à des Solutions Office  
 L'octroi de niveaux de confiance à des solutions Office implique de modifier la stratégie de sécurité de chaque utilisateur final pour approuver la solution Office sur la base des éléments suivants :  
  
-   le certificat utilisé pour signer le manifeste de déploiement,  
  
-   l'URL du manifeste de déploiement.  
  
 Pour plus d’informations, consultez [l’octroi de confiance à des Solutions Office](../vsto/granting-trust-to-office-solutions.md).  
  
##  <a name="GrantingTrustToDocuments"></a>Accorder la confiance à des Documents  
 Pour une personnalisation au niveau du document, le document doit se trouver dans un répertoire désigné comme un emplacement approuvé. Pour plus d'informations, consultez [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
##  <a name="GrantingTrustWindowsInstaller"></a>Octroi d’approbation lors de l’utilisation de Windows Installer  
 Vous pouvez utiliser Windows Installer pour créer un fichier MSI afin d'installer des solutions Office dans le répertoire Program Files, ce qui requiert des droits d'administrateur. Pour les solutions Office dans le répertoire Program Files, Visual Studio 2010 Tools pour Office Runtime considère ces solutions Office fiables et n’affiche pas l’invite d’approbation ClickOnce.  
  
##  <a name="Security"></a>Considérations de sécurité spécifiques pour les Solutions Office  
 Les fonctionnalités de sécurité fournies par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] et Microsoft Office peuvent aider à protéger contre diverses menaces possibles pour la sécurité dans les solutions Office. Pour plus d'informations, consultez [Specific Security Considerations for Office Solutions](../vsto/specific-security-considerations-for-office-solutions.md).  
  
##  <a name="SecurityDuringDeployment"></a>Sécurité pendant le développement  
 Pour faciliter votre processus de développement, Visual Studio définit la stratégie de sécurité requise pour exécuter et déboguer votre solution sur votre ordinateur chaque fois que vous générez un projet. Dans certains scénarios, le développement du projet pourra nécessiter des étapes de sécurité supplémentaires.  
  
### <a name="document-level-solutions"></a>Solutions au niveau du document  
 Le chemin d’accès complet d’un document doit être ajouté à la liste des emplacements approuvés dans l’application Microsoft Office si vous développez les types de projets suivants :  
  
-   Qui se trouvent sur un partage de fichiers réseau tel que les solutions au niveau du document  *\\\servername\sharename*.  
  
-   solutions au niveau du document pour Word qui utilisent des fichiers .doc ou .docm.  
  
 Incluez les sous-répertoires quand vous ajoutez l’emplacement du document à la liste des emplacements approuvés, ou incluez spécifiquement les dossiers de débogage et de génération. Pour plus d’informations, consultez l’article d’aide en ligne de Microsoft Office [créer, supprimer ou modifier un emplacement approuvé pour vos fichiers](https://support.office.com/en-au/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
### <a name="temporary-certificates"></a>Certificats temporaires  
 Visual Studio crée un certificat temporaire si un certificat de signature n'existe pas encore. Vous devez utiliser ce certificat temporaire uniquement pendant le développement et acheter un certificat officiel pour le déploiement.  
  
 Le certificat temporaire est généré après la génération initiale d'un projet Office. Quand vous appuyez une nouvelle fois sur F5, le projet est régénéré car il est marqué comme modifié lors de l'ajout du certificat.  
  
 Il est conseillé de supprimer les certificats temporaires de temps à autre car leur nombre peut augmenter fortement.  
  
##  <a name="VisualStudioToolsForOfficeRuntime"></a>Visual Studio Tools pour Office Runtime  
 Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] propose des fonctionnalités permettant de vérifier l’identité de l’éditeur et les autorisations sont accordées à une personnalisation. Il vérifie ces autorisations via une série de vérifications de sécurité.  
  
### <a name="security-during-customization-loading"></a>Sécurité pendant le chargement de la personnalisation  
 Lors du chargée d’une personnalisation au niveau du document, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vérifie toujours si le document figure dans la liste des emplacements approuvés. En outre, le runtime vérifie si la solution nécessite une confiance totale dans le manifeste d’application. Il n'effectue aucune vérification de la sécurité supplémentaire pendant le chargement de la personnalisation.  
  
### <a name="sequence-of-security-checks-during-installation"></a>Série de vérifications de sécurité pendant l'installation  
 Quand une solution Office est installée ou mise à jour, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] exécute un ensemble de vérifications de sécurité dans un ordre spécifique pour prendre une décision d'approbation. Une solution est installée ou mise à jour seulement si le runtime détermine que la solution est approuvée.  
  
 Vous pouvez démarrer le processus d'installation de quatre manières : en exécutant le programme d'installation, en ouvrant le manifeste de déploiement, en ouvrant l'hôte d'application Microsoft Office ou en exécutant VSTOInstaller.exe.  
  
 La première vérification de sécurité s'applique uniquement aux solutions au niveau du document. Le document d'une solution au niveau du document doit être dans un emplacement approuvé. Si le document se trouve sur un partage de fichiers réseau distant ou possède une extension de nom de fichier .doc ou .docm, l’emplacement du document doit être ajouté à la liste des emplacements approuvés. Pour plus d'informations, consultez [Granting Trust to Documents](../vsto/granting-trust-to-documents.md).  
  
 ![Sécurité VSTO - installation à partir de Microsoft Office](../vsto/media/host-install.png "sécurité VSTO - installation à partir de Microsoft Office")  
  
 L'ensemble de vérifications de sécurité suivant est effectué par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] et ClickOnce. Pour satisfaire à ces vérifications, les solutions Office doivent demander des autorisations FullTrust, être signées avec un certificat qui ne figure pas dans la liste des éditeurs non approuvés et se trouver dans un emplacement qui n’est pas dans la zone limitée d’Internet Explorer. Si le certificat est dans la liste des éditeurs approuvés, la solution est installée immédiatement. Sinon, si elle a satisfait à toutes ces vérifications, le dernier ensemble de vérifications est appliqué.  
  
 ![Sécurité VSTO pour l’installation de solutions](../vsto/media/installing.png "sécurité VSTO pour l’installation de solutions")  
  
 Si le [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation est autorisée et la solution n’a pas encore été approuvée, le runtime autorisera la décision d’approbation doit être effectuée par l’utilisateur final. Si l'utilisateur approuve la solution, une entrée est ajoutée dans la liste d'inclusions de l'utilisateur. Toutes les solutions répertoriées dans la liste d'inclusions de l'utilisateur disposent d'un niveau de confiance totale et peuvent être installées et exécutées.  
  
 À partir de Visual Studio 2010, la liste d'inclusions est ignorée si la solution Office est installée à l'aide de Windows Installer (MSI) dans le répertoire Program Files. Pour plus d’informations, consultez [faire confiance à des Solutions Office à l’utilisation de listes d’Inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 ![Sécurité VSTO - utilisation du programme d’installation pour installer](../vsto/media/setup-vstoinstaller.png "sécurité VSTO - utilisation du programme d’installation pour installer")  
  
## <a name="see-also"></a>Voir aussi  
 [Accorder la confiance à des Solutions Office](../vsto/granting-trust-to-office-solutions.md)   
 [Accorder la confiance à des Documents](../vsto/granting-trust-to-documents.md)   
 [Approbation des Solutions Office à l’aide des listes d’Inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Comment : configurer la sécurité de la liste d’Inclusion](../vsto/how-to-configure-inclusion-list-security.md)   
 [Comment : signer des Solutions Office](../vsto/how-to-sign-office-solutions.md)   
 [Résolution des problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifestes de déploiement pour les Solutions Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Référence de ClickOnce](/visualstudio/deployment/clickonce-reference)   
 [Déploiement d’une solution Office](../vsto/deploying-an-office-solution.md)  
  
  