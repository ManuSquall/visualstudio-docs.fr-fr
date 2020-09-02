---
title: Valeurs de la métrique du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code metrics
- code analysis
- measure code quality
ms.assetid: bc38831e-2083-4ea4-8527-ee41499a342f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23dba7b7c29c05b55af2c461f36bdaa4b46b948f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667719"
---
# <a name="code-metrics-values"></a>Valeurs de la métrique du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La métrique du code est un jeu de mesures de logiciel qui fournit aux développeurs plus de détails sur le code qu'ils développent. En tirant parti des métriques du code, les développeurs peuvent comprendre quels types et/ou méthodes doivent être retravaillés ou être testés de manière plus approfondie. Les équipes de développement peuvent identifier les risques potentiels, comprendre l’état actuel d’un projet et suivre la progression pendant le développement de logiciels.

## <a name="software-measurements"></a>Mesures des logiciels
 La liste suivante répertorie les résultats de la métrique du code qui [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] calcule :

- **Index de maintenabilité** : calcule une valeur d’index comprise entre 0 et 100 qui représente la simplicité relative de la gestion du code. Une valeur élevée signifie une meilleure maintenabilité. Les évaluations codées en couleurs peuvent être utilisées pour identifier rapidement les zones problématiques dans votre code. Une évaluation verte est comprise entre 20 et 100 et indique que le code a une bonne maintenabilité. Une évaluation jaune est comprise entre 10 et 19 et indique que le code peut être géré de façon modérée. Une évaluation rouge est une évaluation comprise entre 0 et 9 et indique une maintenabilité faible.

- **Complexité cyclomatic** : mesure la complexité structurelle du code. Elle est créée en calculant le nombre de chemins de code différents dans le déroulement du programme. Un programme qui a un contrôle de workflow complexe nécessitera davantage de tests pour obtenir une bonne couverture du code et sera moins gérable.

    > [!NOTE]
    > Dans certains cas, le calcul de la complexité cyclomatic pour une méthode dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] diffère des versions antérieures. Pour plus d’informations, consultez la section « modifications de Visual Studio 2010 dans le calcul de complexité du code » de [résolution des problèmes de métriques du code](../code-quality/troubleshooting-code-metrics-issues.md).

- **Profondeur d’héritage** : indique le nombre de définitions de classe qui s’étendent à la racine de la hiérarchie de classes. Plus la hiérarchie est profonde, plus il est difficile de comprendre où des méthodes et des champs particuliers sont définis ou/et redéfinis.

- **Couplage de classe** : mesure le couplage à des classes uniques via des paramètres, des variables locales, des types de retour, des appels de méthode, des instanciations génériques ou de modèle, des classes de base, des implémentations d’interface, des champs définis sur des types externes et une décoration d’attribut. Une bonne conception logicielle impose que les types et les méthodes aient une cohésion élevée et un faible couplage. Le couplage élevé indique une conception qui est difficile à réutiliser et à gérer en raison de ses nombreuses interdépendances sur d’autres types.

- **Lignes de code** : indique le nombre approximatif de lignes dans le code. Le nombre est basé sur le code IL et n’est donc pas le nombre exact de lignes dans le fichier de code source. Un nombre très élevé peut indiquer qu’un type ou une méthode tente de faire trop de travail et doit être fractionné. Il peut également indiquer que le type ou la méthode peut être difficile à gérer.

## <a name="anonymous-methods"></a>Méthodes anonymes
 Une *méthode anonyme* est simplement une méthode qui n’a pas de nom. Les méthodes anonymes sont le plus souvent utilisées pour passer un bloc de code en tant que paramètre de délégué. Les résultats des métriques pour une méthode anonyme déclarée dans un membre, tel qu’une méthode ou un accesseur, sont associés au membre qui déclare la méthode. Ils ne sont pas associés au membre qui appelle la méthode.

 Pour plus d’informations sur la façon dont les métriques du Code traitent les méthodes anonymes, consultez [méthodes anonymes et analyse du code](../code-quality/anonymous-methods-and-code-analysis.md).

## <a name="generated-code"></a>Code généré
 Certains outils et compilateurs logiciels génèrent du code qui est ajouté à un projet et qui ne sont pas visibles ou ne doivent pas être modifiés par le développeur du projet. En majorité, les métriques du code ignorent le code généré lorsqu’il calcule les valeurs de métriques. Cela permet aux valeurs de métriques de refléter ce que le développeur peut voir et modifier.

 Le code généré pour Windows Forms n’est pas ignoré, car il s’agit d’un code que le développeur peut voir et modifier.

## <a name="see-also"></a>Voir aussi
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
