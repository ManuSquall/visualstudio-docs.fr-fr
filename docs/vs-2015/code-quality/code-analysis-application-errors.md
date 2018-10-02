---
title: Erreurs d’Application d’analyse de code | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio ALM], code analysis
- code analysis, errors
- managed code, code analysis errors
- code analysis, policy errors
ms.assetid: d8fd9475-ac9b-4085-b5a3-b0c807922cac
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f33e8cf139193618cfe8fe45d916ec59b38a74c1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494553"
---
# <a name="code-analysis-application-errors"></a>Erreurs d’application d’analyse du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [erreurs d’analyse du Code d’Application](https://docs.microsoft.com/visualstudio/code-quality/code-analysis-application-errors).

Cette section est une référence des messages d’erreur générés par l’outil d’analyse du code managé. Pour obtenir une aide pour un message d’erreur spécifique, tapez le numéro d’erreur dans le **recherchez** zone dans l’Index.

## <a name="in-this-section"></a>Dans cette section

|||
|-|-|
|[CA0001](ca0001.md)|Une exception a été levée dans l’outil d’analyse du code managé qui n’indique pas une condition d’erreur attendue.|
|[CA0051](ca0051.md)|Aucune règle n’a été sélectionné.|
|[CA0052](ca0052.md)|Aucune cible n’a été sélectionné pour l’analyse.|
|[CA0053](ca0053.md)|Assembly de règle n’a pas pu être chargé.|
|[CA0054](ca0054.md)|Un assembly de règle personnalisé possède des ressources XML.|
|[CA0055](ca0055.md)|Fichier n’a pas pu être charger :\<chemin d’accès >|
|[CA0056](ca0056.md)|Un fichier de projet a une version incorrecte de l’outil d’analyse.|
|[CA0057](ca0057.md)|Violations ne peut pas être mappées à l’ensemble actuel de cibles et de règles.|
|[CA0058](ca0058.md)|Impossible de charger les assemblys référencés.|
|[CA0059](ca0059.md)|Erreur du commutateur de ligne de commande.|
|[CA0060](ca0060.md)|Impossible de charger les assemblys référencés indirectement.|
|[CA0061](ca0061.md)|La règle «*RuleId*' est introuvable.|
|[CA0062](ca0062.md)|La règle «*RuleId*« référencée dans l’ensemble de règles »*RuleSetName*» est introuvable.|
|[CA0063](ca0063.md)|Échec du chargement du fichier d’ensemble de règles ou l’un de ses fichiers d’ensembles de règles dépendants.|
|[CA0064](ca0064.md)|Aucune analyse n’a été effectuée car l’ensemble de règles spécifiée ne contenait pas toutes les règles FxCop.|
|[CA0065](ca0065.md)|Construction de métadonnées non pris en charge : Type '*TypeName*'contient une propriété et un champ portant le même nom'*NomChampPropriété*'|
|[CA0066](ca0066.md)|La valeur '*VersionID*' fourni pour le **/TargetFrameworkVersion ne** n’est pas une version reconnue.|
|[CA0067](ca0067.md)|Répertoire introuvable.|
|[CA0068](ca0068.md)|Déboguer des informations n’a pas pu être trouvées pour l’assembly cible *'Nom_assembly'*.|
|[CA0069](ca0069.md)|À l’aide de la plateforme autre. *FrameworkVersion1* est introuvable. À l’aide de *Versionframework2* à la place. Pour obtenir de meilleurs résultats d’analyse Assurez-vous que le .NET Framework approprié est installé.|
|[CA0070](ca0070.md)|Ne peut pas charger l’assembly ou un type en raison d’autorisations de sécurité.|
|[CA0501](ca0501.md)|Impossible de lire le rapport de sortie.|
|[CA0502](ca0502.md)|Langage non pris en charge.|
|[CA0503](ca0503.md))|La propriété est déconseillée. Utilisez la propriété de remplacement|
|[CA0504](ca0504.md)|Répertoire de règle a été ignoré, car il n’existe pas|
|[CA0505](ca0505.md)|La propriété est déconseillée. Utilisez la propriété de remplacement|
|[Erreurs FxCopCmd](fxcopcmd-errors.md)|Erreurs d’analyse du code managé.|
|[Code Analysis Policy Errors](../code-quality/code-analysis-policy-errors.md)|Code de vérification de l’analyse des erreurs de stratégie.|

## <a name="related-sections"></a>Rubriques connexes

- [Instructions pour l’écriture de Code sécurisé](http://msdn.microsoft.com/en-us/9892fd19-45cd-44b6-9fa8-10f1b5cb6ea4)
- [Analyse de la qualité d’un code managé](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
- [Ressources pour la résolution des erreurs dans les outils de gestion du cycle de vie des applications](http://msdn.microsoft.com/library/76ca8f76-1e2d-4b55-89e2-bd59e4abe74c)