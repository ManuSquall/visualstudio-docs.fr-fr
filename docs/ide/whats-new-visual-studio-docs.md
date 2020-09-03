---
title: 'Documentation de Visual Studio : nouveautés du 2020 août '
titleSuffix: ''
description: Nouveautés de Visual Studio docs pour le 2020 août.
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 4364bd62ac19be958632b8cb2dbbe907013e8a70
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402242"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Documentation de Visual Studio : nouveautés du 2020 août

Bienvenue dans les documents sur les nouveautés de Visual Studio pour le 2020 août. Cet article répertorie les principales modifications apportées à la documentation au cours de cette période. Pour plus d’informations sur les nouveautés des mois précédents, consultez la rubrique nouveautés de l' [historique](whats-new-visual-studio-docs-history.md) .

## <a name="azure"></a>Azure

**Nouveaux Articles**

- [Ajoutez Azure application Insights à l’aide](/visualstudio/azure/azure-app-insights-add-connected-service) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajouter le cache Azure pour les éléments ReDim à l’aide](/visualstudio/azure/azure-cache-for-redis-add-connected-service) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajoutez des Azure Cosmos dB à votre application à l’aide](/visualstudio/azure/azure-cosmosdb-add-connected-service) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajouter Azure signalr à l’aide](/visualstudio/azure/azure-signalr-add-connected-service) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajouter une connexion aux services connectés à Azure SQL Database](/visualstudio/azure/azure-sql-database-add-connected-service) pour VS 2019 16,7

**Articles mis à jour**

- [Ajout de stockage Azure à l’aide des services connectés de Visual Studio](/visualstudio/azure/vs-azure-tools-connected-services-storage)
  - Services connectés pour VS 2019 16,7
  - Article sur les services connectés Azure Storage : mise à jour des types de projet et d’interface utilisateur pris en charge

## <a name="code-quality"></a>Qualité du code

**Nouveaux Articles**

- [Ca1310 : spécifiez StringComparison pour l’exactitude](/visualstudio/code-quality/ca1310) -ajoutez de la documentation pour ca1310 et mettez à jour la documentation pour CA1307
- [CA1837 : utilisez Environment. ProcessID au lieu de process. GetCurrentProcess (). ID](/visualstudio/code-quality/ca1837) -docs pour CA1837
- [CA1838 : éviter `StringBuilder` les paramètres pour P/Invoke](/visualstudio/code-quality/ca1838) -ajouter de la documentation pour CA1838
- [CA2008 : ne pas créer de tâches sans passer un TaskScheduler](/visualstudio/code-quality/ca2008) -ajouter une documentation pour CA2008
- [CA2249 : envisagez d’utiliser String. Contains à la place de String. IndexOf](/visualstudio/code-quality/ca2249) -docs pour CA2249
- [CA2361 : Assurez-vous que la classe générée automatiquement contenant DataSet. ReadXml () n’est pas utilisée avec des données non fiables.](/visualstudio/code-quality/ca2361) autres règles de DataSet/DataTable
- [CA2362 : un jeu de données ou un DataTable non sécurisé dans un type sérialisable généré automatiquement peut être vulnérable aux attaques d’exécution de code à distance](/visualstudio/code-quality/ca2362) . autres règles de DataSet/DataTable
- [IL3000 : Évitez d’utiliser le chemin d’accès au fichier d’assembly lors de la publication en tant que documentation à fichier unique](/visualstudio/code-quality/il3000) à ajouter à IL3000
- [IL3001 : éviter d’accéder au chemin d’accès au fichier d’assembly lors de la publication sous la forme d’un fichier unique](/visualstudio/code-quality/il3001) -ajouter des documents pour IL3001

**Updated**

- [Ca1002 : ne pas exposer les listes génériques](/visualstudio/code-quality/ca1002) -ajouter la configuration-section de surface de l’API
- [Ca1046 : ne pas surcharger l’opérateur égal à sur les types référence](/visualstudio/code-quality/ca1046) -ajouter la configuration-section surface de l’API
- [CA1307 : spécifiez StringComparison pour clarifier](/visualstudio/code-quality/ca1307) -ajouter de la documentation pour ca1310 et mettre à jour la documentation pour CA1307
- [CA1700 : ne nommez pas les valeurs enum &#39;réservé&#39;](/visualstudio/code-quality/ca1700) -Add configurabilité-API surface
- [CA1707 : les identificateurs ne doivent pas contenir de traits de soulignement](/visualstudio/code-quality/ca1707) -ajouter une configuration-section de surface de l’API
- [CA1822 : marquer les membres comme statiques](/visualstudio/code-quality/ca1822) -ajouter une configuration-section surface de l’API
- [Ca2351 : Assurez-vous que l’entrée de DataSet. ReadXml () est approuvée](/visualstudio/code-quality/ca2351) -plus de règles de DataSet/DataTable
- [Installer des analyseurs tiers](/visualstudio/code-quality/install-roslyn-analyzers) -modification de la structure et des titres pour la documentation de l’analyse du code

## <a name="containers"></a>Containers

**Articles mis à jour**

- [Déployer un conteneur ASP.net dans un registre de conteneurs à l’aide de Visual Studio](/visualstudio/containers/hosting-web-apps-in-docker) -mises à jour des outils de conteneur pour l’interface utilisateur de publication de visual studio 16,7
- [Prise en main de Visual Studio Kubernetes Tools](/visualstudio/containers/tutorial-kubernetes-tools) -didacticiel Kubernetes : ajouter des étapes de suppression

## <a name="deployment"></a>Déploiement

**Nouveaux Articles**

- [Extension des projets Visual Studio installer et .net core 3,1](/visualstudio/deployment/installer-projects-net-core) -création d’une nouvelle page d’aide pour les projets du programme d’installation fonctionnalités .net Core 3,1

**Articles mis à jour**

- [Déployer votre application dans un dossier, IIS, Azure ou une autre](/visualstudio/deployment/deploying-applications-services-and-components-resources) mise à jour de destination-déploiement
- [Déploiement dans Visual Studio](/visualstudio/deployment/index) -mises à jour du déploiement

## <a name="extensibility"></a>Extensibilité

**Articles mis à jour**
- Sous- [types de projet](/visualstudio/extensibility/internals/project-subtypes) -mettre en retrait les éléments de liste
- [Référence de valeur de couleur pour Visual Studio](/visualstudio/extensibility/ux-guidelines/color-value-reference-for-visual-studio) -AB # 1759333 corriger les en-têtes de colonnes manquantes

## <a name="get-started"></a>Bien démarrer

**Articles mis à jour**

- [Étape 5 : déployer votre application ASP.net core dans Azure](/visualstudio/get-started/csharp/tutorial-aspnet-core-ef-step-05) -mises à jour des didacticiels vidéo pour les nouvelles services connectés IU

## <a name="ide"></a>IDE

**Nouveaux Articles**

- [Modifier la touche d’aide F1 dans Visual Studio](/visualstudio/ide/not-in-toc/change-f1-help-key) -page d’aide par défaut de refactorisation F1
- [Aide F1 pour l’éditeur de texte](/visualstudio/ide/not-in-toc/default-f1-text-editor) -page d’aide F1 par défaut de refactorisation
- [Convertir `typeof` en `nameof` ](/visualstudio/ide/reference/convert-typeof-to-nameof) -Convert typeof en refactorisation nameof
- [Simplifier l’expression LINQ](/visualstudio/ide/reference/simplify-linq-expression) -simplifier la refactorisation d’expression LINQ

**Articles mis à jour**

- [Personnaliser les dispositions de fenêtres dans Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio) : ajouter des onglets de document monikered verticaux info pour personnaliser la rubrique disposition des fenêtres
- [Guide pratique pour signaler un problème avec Visual Studio ou Visual Studio Installer](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
  - Ajout d’informations supplémentaires à NMI
  - Redid la page de l’ensemble du rapport
- [Aide F1](/visualstudio/ide/not-in-toc/default) -page d’aide par défaut de refactorisation F1
- [Récupération automatique, environnement, boîte de dialogue Options](/visualstudio/ide/reference/autorecover-environment-options-dialog-box) -ajouter des informations sur les emplacements de fichiers d’enregistrement automatique mis à jour
- [Options, éditeur de texte, de base (Visual Basic), avancé](/visualstudio/ide/reference/options-text-editor-basic-visual-basic) -ajout de la documentation de base pour les indicateurs de nom de paramètre Inline
- [Options, éditeur de texte, C#,](/visualstudio/ide/reference/options-text-editor-csharp-advanced) documentation de base ajoutée pour les indicateurs de nom de paramètre Inline
- [Conseils et astuces sur les performances de Visual Studio](/visualstudio/ide/visual-studio-performance-tips-and-tricks) : ajouter les informations « désactiver le mode carte » et « désactiver le retour automatique à la ligne »
- [Nouveautés de Visual studio 2019](/visualstudio/ide/whats-new-visual-studio-2019) -mettre à jour nouveautés dans visual studio 2019 avec 16,7 informations sur la disponibilité générale

## <a name="rtvs"></a>RTVS

**Articles mis à jour**

- [Utiliser des tables SQL Server et R](/visualstudio/rtvs/integrating-sql-server-with-r) -corrigées pour inclure des en-têtes de colonnes

## <a name="community-contributors"></a>Contributeurs de la communauté

Les personnes suivantes ont participé à la documentation de Visual Studio pendant cette période. Merci ! Découvrez comment contribuer à la documentation de Visual Studio en suivant les instructions du [Guide du contributeur](https://docs.microsoft.com/contribute/).

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG) -Alex noir (11)
- [Youssef1313](https://github.com/Youssef1313) -youssef Victor (8)
- [hyoshioka0128](https://github.com/hyoshioka0128) -Hiroshi Yoshioka (3)
- [AstroChoco](https://github.com/AstroChoco) -Qian lu (chocolat) (1)
- [athyunnath](https://github.com/athyunnath) -athyunnath Eleti (1)
- [Caro-Oviedo](https://github.com/caro-oviedo) -Caro Oviedo (1)
- [Evangelink](https://github.com/Evangelink) -Amaury levé (1)
- [jethas-bennettjones](https://github.com/jethas-bennettjones) -Shafiq Jetha (1)
- [nebuk89](https://github.com/nebuk89) -Ben de St PAER-Gotch (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov) -Petr Kulikov (1)
- [riQQ](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger) -Timo Cornelius Metzger (1)
- [Weitzhandler](https://github.com/weitzhandler) -shim (1)