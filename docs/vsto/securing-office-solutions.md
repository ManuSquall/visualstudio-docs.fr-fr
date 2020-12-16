---
title: Sécuriser les solutions Office
description: Découvrez comment le modèle de sécurité pour les solutions Office implique plusieurs technologies, notamment le Visual Studio Tools pour Office Runtime et ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- security [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bedb49a6d5d17e3c9f79a652183c2b4cd748ff6c
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528481"
---
# <a name="secure-office-solutions"></a>Sécuriser les solutions Office
  Le modèle de sécurité pour les solutions Office implique plusieurs technologies : [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] , le centre de gestion de la confidentialité dans Microsoft Office et la zone sites sensibles d’Internet Explorer. Les sections suivantes décrivent le fonctionnement de ces différentes fonctionnalités de sécurité :

- [Accorder un niveau de confiance à des solutions Office](#GrantingTrustToSolutions)

- [Accorder un niveau de confiance à des documents](#GrantingTrustToDocuments)

- [Accorder une confiance lors de l’utilisation de Windows Installer](#GrantingTrustWindowsInstaller)

- [Considérations de sécurité spécifiques pour les solutions Office](#Security)

- [Sécurité pendant le développement](#SecurityDuringDeployment)

- [Visual Studio Tools pour Office Runtime](#VisualStudioToolsForOfficeRuntime)

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="grant-trust-to-office-solutions"></a><a name="GrantingTrustToSolutions"></a> Accorder un niveau de confiance à des solutions Office
 L'octroi de niveaux de confiance à des solutions Office implique de modifier la stratégie de sécurité de chaque utilisateur final pour approuver la solution Office sur la base des éléments suivants :

- le certificat utilisé pour signer le manifeste de déploiement,

- l'URL du manifeste de déploiement.

  Pour plus d’informations, consultez accorder un niveau [de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md).

## <a name="grant-trust-to-documents"></a><a name="GrantingTrustToDocuments"></a> Accorder un niveau de confiance à des documents
 Pour une personnalisation au niveau du document, le document doit se trouver dans un répertoire désigné comme un emplacement approuvé. Pour plus d’informations, consultez accorder un niveau [de confiance à des documents](../vsto/granting-trust-to-documents.md).

## <a name="grant-trust-when-using-windows-installer"></a><a name="GrantingTrustWindowsInstaller"></a> Accorder une confiance lors de l’utilisation de Windows Installer
 Vous pouvez utiliser Windows Installer pour créer un fichier MSI afin d'installer des solutions Office dans le répertoire Program Files, ce qui requiert des droits d'administrateur. Pour les solutions Office dans le répertoire Program Files, Visual Studio 2010 Tools pour Office Runtime considère que ces solutions Office sont approuvées et n’affiche pas l’invite d’approbation ClickOnce.

## <a name="specific-security-considerations-for-office-solutions"></a><a name="Security"></a> Considérations de sécurité spécifiques pour les solutions Office
 Les fonctionnalités de sécurité fournies par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] et Microsoft Office peuvent aider à protéger contre diverses menaces possibles pour la sécurité dans les solutions Office. Pour plus d’informations, consultez [considérations de sécurité spécifiques pour les solutions Office](../vsto/specific-security-considerations-for-office-solutions.md).

## <a name="security-during-development"></a><a name="SecurityDuringDeployment"></a> Sécurité pendant le développement
 Pour faciliter votre processus de développement, Visual Studio définit la stratégie de sécurité requise pour exécuter et déboguer votre solution sur votre ordinateur chaque fois que vous générez un projet. Dans certains scénarios, le développement du projet pourra nécessiter des étapes de sécurité supplémentaires.

### <a name="document-level-solutions"></a>Solutions au niveau du document
 Le chemin d’accès complet d’un document doit être ajouté à la liste des emplacements approuvés dans l’application Microsoft Office si vous développez les types de projets suivants :

- Les solutions au niveau du document qui se trouvent sur un partage de fichiers réseau tel que *\\ \nomserveur\nompartage*.

- Solutions au niveau du document pour Word qui utilisent des fichiers *. doc* ou *. docm* .

  Incluez les sous-répertoires quand vous ajoutez l'emplacement du document à la liste des emplacements approuvés, ou incluez spécifiquement les dossiers de débogage et de génération. Pour plus d’informations, consultez l’article d’aide en ligne Microsoft Office [créer, supprimer ou modifier un emplacement approuvé pour vos fichiers](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).

### <a name="temporary-certificates"></a>Certificats temporaires
 Visual Studio crée un certificat temporaire si un certificat de signature n'existe pas encore. Vous devez utiliser ce certificat temporaire uniquement pendant le développement et acheter un certificat officiel pour le déploiement.

 Le certificat temporaire est généré après la génération initiale d'un projet Office. La prochaine fois que vous appuierez sur **F5**, le projet est régénéré car le projet est marqué comme modifié lorsque le certificat est ajouté.

 Il est conseillé de supprimer les certificats temporaires de temps à autre car leur nombre peut augmenter fortement.

## <a name="visual-studio-tools-for-office-runtime"></a><a name="VisualStudioToolsForOfficeRuntime"></a> Visual Studio Tools pour Office Runtime
 Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] possède des fonctionnalités permettant de vérifier l’identité du serveur de publication et les autorisations accordées à une personnalisation. Il vérifie ces autorisations via une série de vérifications de sécurité.

### <a name="security-during-customization-loading"></a>Sécurité lors du chargement de la personnalisation
 Lors du chargement d’une personnalisation au niveau du document, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] vérifie toujours si le document figure dans la liste des emplacements approuvés. En outre, le runtime vérifie si la solution nécessite une confiance totale (FullTrust) dans le manifeste d'application. Il n'effectue aucune vérification de la sécurité supplémentaire pendant le chargement de la personnalisation.

### <a name="sequence-of-security-checks-during-installation"></a>Séquence de vérifications de sécurité au cours de l’installation
 Quand une solution Office est installée ou mise à jour, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] exécute un ensemble de vérifications de sécurité dans un ordre spécifique pour prendre une décision d'approbation. Une solution est installée ou mise à jour seulement si le runtime détermine que la solution est approuvée.

 Vous pouvez démarrer le processus d’installation de quatre manières : en exécutant le programme d’installation, en ouvrant le manifeste de déploiement, en ouvrant l’hôte d’application Microsoft Office ou en exécutant *VSTOInstaller.exe*.

 La première vérification de sécurité s'applique uniquement aux solutions au niveau du document. Le document d'une solution au niveau du document doit être dans un emplacement approuvé. Si le document se trouve sur un partage de fichiers réseau distant ou possède une extension de nom de fichier *. doc* ou *. docm* , l’emplacement du document doit être ajouté à la liste des emplacements approuvés. Pour plus d’informations, consultez accorder un niveau [de confiance à des documents](../vsto/granting-trust-to-documents.md).

 ![Sécurité VSTO - installation à partir de Microsoft Office](../vsto/media/host-install.png "Sécurité VSTO - installation à partir de Microsoft Office")

 L'ensemble de vérifications de sécurité suivant est effectué par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] et ClickOnce. Pour satisfaire à ces vérifications, les solutions Office doivent exiger des autorisations FullTrust, être signées à l'aide d'un certificat qui n'est pas répertorié dans la liste des éditeurs non approuvés et se trouver dans un emplacement qui n'est pas dans la zone limitée d'Internet Explorer. Si le certificat figure dans la liste des éditeurs approuvés, la solution est installée immédiatement. Sinon, si elle a satisfait à toutes ces vérifications, le dernier ensemble de vérifications est appliqué.

 ![Sécurité VSTO pour l'installation de solutions](../vsto/media/installing.png "Sécurité VSTO pour l'installation de solutions")

 Si l' [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] invite d’approbation est autorisée et que la solution n’a pas encore été approuvée, le runtime permettra à l’utilisateur final de prendre la décision d’approbation. Si l'utilisateur approuve la solution, une entrée est ajoutée dans la liste d'inclusions de l'utilisateur. Toutes les solutions répertoriées dans la liste d'inclusions de l'utilisateur disposent d'un niveau de confiance totale et peuvent être installées et exécutées.

 À partir de Visual Studio 2010, la liste d'inclusions est ignorée si la solution Office est installée à l'aide de Windows Installer (MSI) dans le répertoire Program Files. Pour plus d’informations, consultez [approuver des solutions Office à l’aide de listes d’inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).

 ![Sécurité VSTO - utilisation du programme d’installation](../vsto/media/setup-vstoinstaller.png "Sécurité VSTO - utilisation du programme d’installation")

## <a name="see-also"></a>Voir aussi

- [Accorder un niveau de confiance à des solutions Office](../vsto/granting-trust-to-office-solutions.md)
- [Accorder un niveau de confiance à des documents](../vsto/granting-trust-to-documents.md)
- [Approuver des solutions Office à l’aide de listes d’inclusion](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)
- [Comment : configurer la sécurité de la liste d’inclusion](../vsto/how-to-configure-inclusion-list-security.md)
- [Comment : signer des solutions Office](../vsto/how-to-sign-office-solutions.md)
- [Résoudre les problèmes de sécurité des solutions Office](../vsto/troubleshooting-office-solution-security.md)
- [Manifestes d’application pour les solutions Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestes de déploiement pour les solutions Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Référence ClickOnce](../deployment/clickonce-reference.md)
- [Déployer une solution Office](../vsto/deploying-an-office-solution.md)
