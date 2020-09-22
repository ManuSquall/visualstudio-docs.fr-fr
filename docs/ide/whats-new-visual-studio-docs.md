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
ms.openlocfilehash: 2411299fbab6dfba8ced0f689bd33825b62614af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808979"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Documentation de Visual Studio : nouveautés du 2020 août

Bienvenue dans les documents sur les nouveautés de Visual Studio pour le 2020 août. Cet article répertorie les principales modifications apportées à la documentation au cours de cette période. Pour plus d’informations sur les nouveautés des mois précédents, consultez la rubrique nouveautés de l' [historique](whats-new-visual-studio-docs-history.md) .

## <a name="azure"></a>Azure

**Nouveaux Articles**

- [Ajoutez Azure application Insights à l’aide](../azure/azure-app-insights-add-connected-service.md) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajouter le cache Azure pour les éléments ReDim à l’aide](../azure/azure-cache-for-redis-add-connected-service.md) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajoutez des Azure Cosmos dB à votre application à l’aide](../azure/azure-cosmosdb-add-connected-service.md) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajouter Azure signalr à l’aide](../azure/azure-signalr-add-connected-service.md) des services connectés à Visual Studio services connectés pour VS 2019 16,7
- [Ajouter une connexion aux services connectés à Azure SQL Database](../azure/azure-sql-database-add-connected-service.md) pour VS 2019 16,7

**Articles mis à jour**

- [Ajout de stockage Azure à l’aide des services connectés de Visual Studio](../azure/vs-azure-tools-connected-services-storage.md)
  - Services connectés pour VS 2019 16,7
  - Article sur les services connectés Azure Storage : mise à jour des types de projet et d’interface utilisateur pris en charge

## <a name="code-quality"></a>Qualité du code

**Nouveaux Articles**

- [Ca1310 : spécifiez StringComparison pour l’exactitude](../code-quality/ca1310.md) -ajoutez de la documentation pour ca1310 et mettez à jour la documentation pour CA1307
- [CA1837 : utilisez Environment. ProcessID au lieu de process. GetCurrentProcess (). ID](../code-quality/ca1837.md) -docs pour CA1837
- [CA1838 : éviter `StringBuilder` les paramètres pour P/Invoke](../code-quality/ca1838.md) -ajouter de la documentation pour CA1838
- [CA2008 : ne pas créer de tâches sans passer un TaskScheduler](../code-quality/ca2008.md) -ajouter une documentation pour CA2008
- [CA2249 : envisagez d’utiliser String. Contains à la place de String. IndexOf](../code-quality/ca2249.md) -docs pour CA2249
- [CA2361 : Assurez-vous que la classe générée automatiquement contenant DataSet. ReadXml () n’est pas utilisée avec des données non fiables.](../code-quality/ca2361.md) autres règles de DataSet/DataTable
- [CA2362 : un jeu de données ou un DataTable non sécurisé dans un type sérialisable généré automatiquement peut être vulnérable aux attaques d’exécution de code à distance](../code-quality/ca2362.md) . autres règles de DataSet/DataTable
- [IL3000 : Évitez d’utiliser le chemin d’accès au fichier d’assembly lors de la publication en tant que documentation à fichier unique](../code-quality/il3000.md) à ajouter à IL3000
- [IL3001 : éviter d’accéder au chemin d’accès au fichier d’assembly lors de la publication sous la forme d’un fichier unique](../code-quality/il3001.md) -ajouter des documents pour IL3001

**Updated**

- [Ca1002 : ne pas exposer les listes génériques](../code-quality/ca1002.md) -ajouter la configuration-section de surface de l’API
- [Ca1046 : ne pas surcharger l’opérateur égal à sur les types référence](../code-quality/ca1046.md) -ajouter la configuration-section surface de l’API
- [CA1307 : spécifiez StringComparison pour clarifier](../code-quality/ca1307.md) -ajouter de la documentation pour ca1310 et mettre à jour la documentation pour CA1307
- [CA1700 : ne nommez pas les valeurs enum &#39;réservé&#39;](../code-quality/ca1700.md) -Add configurabilité-API surface
- [CA1707 : les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707.md) -ajouter une configuration-section de surface de l’API
- [CA1822 : marquer les membres comme statiques](../code-quality/ca1822.md) -ajouter une configuration-section surface de l’API
- [Ca2351 : Assurez-vous que l’entrée de DataSet. ReadXml () est approuvée](../code-quality/ca2351.md) -plus de règles de DataSet/DataTable
- [Installer des analyseurs tiers](../code-quality/install-roslyn-analyzers.md) -modification de la structure et des titres pour la documentation de l’analyse du code

## <a name="containers"></a>Conteneurs

**Articles mis à jour**

- [Déployer un conteneur ASP.net dans un registre de conteneurs à l’aide de Visual Studio](../containers/hosting-web-apps-in-docker.md) -mises à jour des outils de conteneur pour l’interface utilisateur de publication de visual studio 16,7
- [Prise en main de Visual Studio Kubernetes Tools](../containers/tutorial-kubernetes-tools.md) -didacticiel Kubernetes : ajouter des étapes de suppression

## <a name="deployment"></a>Déploiement

**Nouveaux Articles**

- [Extension des projets Visual Studio installer et .net core 3,1](../deployment/installer-projects-net-core.md) -création d’une nouvelle page d’aide pour les projets du programme d’installation fonctionnalités .net Core 3,1

**Articles mis à jour**

- [Déployer votre application dans un dossier, IIS, Azure ou une autre](../deployment/deploying-applications-services-and-components-resources.md) mise à jour de destination-déploiement
- [Déploiement dans Visual Studio](../deployment/index.yml) -mises à jour du déploiement

## <a name="extensibility"></a>Extensibilité

**Articles mis à jour**
- Sous- [types de projet](../extensibility/internals/project-subtypes.md) -mettre en retrait les éléments de liste
- [Référence de valeur de couleur pour Visual Studio](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) -AB # 1759333 corriger les en-têtes de colonnes manquantes

## <a name="get-started"></a>Commencer

**Articles mis à jour**

- [Étape 5 : déployer votre application ASP.net core dans Azure](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) -mises à jour des didacticiels vidéo pour les nouvelles services connectés IU

## <a name="ide"></a>IDE

**Nouveaux Articles**

- [Modifier la touche d’aide F1 dans Visual Studio](./not-in-toc/change-f1-help-key.md) -page d’aide par défaut de refactorisation F1
- [Aide F1 pour l’éditeur de texte](./not-in-toc/default-f1-text-editor.md) -page d’aide F1 par défaut de refactorisation
- [Convertir `typeof` en `nameof` ](./reference/convert-typeof-to-nameof.md) -Convert typeof en refactorisation nameof
- [Simplifier l’expression LINQ](./reference/simplify-linq-expression.md) -simplifier la refactorisation d’expression LINQ

**Articles mis à jour**

- [Personnaliser les dispositions de fenêtres dans Visual Studio](./customizing-window-layouts-in-visual-studio.md) : ajouter des onglets de document monikered verticaux info pour personnaliser la rubrique disposition des fenêtres
- [Guide pratique pour signaler un problème avec Visual Studio ou Visual Studio Installer](./how-to-report-a-problem-with-visual-studio.md)
  - Ajout d’informations supplémentaires à NMI
  - Redid la page de l’ensemble du rapport
- [Aide F1](./not-in-toc/default.md) -page d’aide par défaut de refactorisation F1
- [Récupération automatique, environnement, boîte de dialogue Options](./reference/autorecover-environment-options-dialog-box.md) -ajouter des informations sur les emplacements de fichiers d’enregistrement automatique mis à jour
- [Options, éditeur de texte, de base (Visual Basic), avancé](./reference/options-text-editor-basic-visual-basic.md) -ajout de la documentation de base pour les indicateurs de nom de paramètre Inline
- [Options, éditeur de texte, C#,](./reference/options-text-editor-csharp-advanced.md) documentation de base ajoutée pour les indicateurs de nom de paramètre Inline
- [Conseils et astuces sur les performances de Visual Studio](./visual-studio-performance-tips-and-tricks.md) : ajouter les informations « désactiver le mode carte » et « désactiver le retour automatique à la ligne »
- [Nouveautés de Visual studio 2019](./whats-new-visual-studio-2019.md) -mettre à jour nouveautés dans visual studio 2019 avec 16,7 informations sur la disponibilité générale

## <a name="rtvs"></a>RTVS

**Articles mis à jour**

- [Utiliser des tables SQL Server et R](../rtvs/integrating-sql-server-with-r.md) -corrigées pour inclure des en-têtes de colonnes

## <a name="community-contributors"></a>Contributeurs de la communauté

Les personnes suivantes ont participé à la documentation de Visual Studio pendant cette période. Merci ! Découvrez comment contribuer à la documentation de Visual Studio en suivant les instructions du [Guide du contributeur](/contribute/).

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