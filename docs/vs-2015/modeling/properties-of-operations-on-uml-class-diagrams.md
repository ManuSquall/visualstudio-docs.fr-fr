---
title: Propriétés des opérations sur les diagrammes de classes UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d752fa802deef5dcc40fdfa4d762dc6edb1d0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671353"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Propriétés d'opérations dans des diagrammes de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sur un diagramme de classes UML, vous pouvez ajouter des *opérations* à des classes et des interfaces. Une opération est une méthode ou une fonction qui peut être exécutée par une instance d'une classe ou d'une interface.

 Pour ajouter une opération, cliquez avec le bouton droit sur la classe ou l’interface, pointez sur **Ajouter**, puis cliquez sur **opération**.

 Si les opérations d'une classe ne sont pas visibles dans le diagramme, cliquez sur le chevron de développement situé en haut de la classe ou de l'interface. Si vous pouvez voir l’en-tête de l' **opération** , cliquez sur **[+]** pour développer la section opérations.

## <a name="signature-of-an-operation"></a>Signature d'une opération
 La signature d'une opération est la ligne de texte qui le représente dans une classe ou une interface dans un diagramme de classes UML. Son format est le suivant :

 \+ NomOpération (paramètre1 : type1 [*],...) : ReturnType [\*]

 \+ indique une visibilité publique. Les autres valeurs autorisées sont - (privé), # (protégé), ~ (package).

 `OperationName` est souligné si la propriété **is static** a la valeur true, et est en italique si la propriété **is abstract** a la valeur true.

 `: ReturnType` est omis si aucun type de retour n'est défini.

 `[*]` indique la multiplicité d'un paramètre ou d'un type de retour. Il est omis si la multiplicité est de 1.

 Pour obtenir une description complète de ces propriétés, consultez la section suivante.

## <a name="properties"></a>Propriétés
 Il s'agit des propriétés d'une opération dans une classe ou une interface dans un diagramme de classes UML.

 Pour afficher les propriétés d’une opération, cliquez avec le bouton droit sur l’opération dans la classe ou l’interface sur le diagramme, puis cliquez sur **Propriétés**. Les propriétés s’affichent dans la fenêtre **Propriétés** .

|      Property       |   Valeur par défaut    |                                                                                                                                                                                 Description                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Nom**       | (un nouveau nom) |                                                                                                                                                                Doit être unique dans le type conteneur.                                                                                                                                                                 |
|   **Paramètres**    |    (aucune)    |      Liste sous la forme <em>nom</em> **:** <em>type</em> **,** <em>nom</em> **:** <em>type</em> **,....** Cliquez sur **[...]** pour modifier la liste.<br /><br /> Les types peuvent être des types primitifs ou des types définis dans le modèle. Si vous entrez un nom pour un nouveau type dans cette propriété, un type est ajouté à la section **Types non spécifiés** de l’Explorateur de modèles UML.      |
|   **Type de retour**   |    (aucune)    |                                                                               **(None)** , ou un type primitif, ou un type défini dans le modèle. Si vous entrez un nom pour un nouveau type dans cette propriété, un type est ajouté à la section **Types non spécifiés** de l’Explorateur de modèles UML.                                                                                |
| **Conditions**  |    (aucune)    |                                                                                                                         Condition facultative spécifiant une relation entre l'état du système avant et après l'exécution de l'opération.                                                                                                                         |
|  **Conditions préalables**  |    (aucune)    |                                                                                                                            Condition facultative spécifiant les hypothèses concernant l'état du système avant l'exécution de l'opération.                                                                                                                            |
| **Conditions du corps** |    (aucune)    |                                                                                                                                                       Contrainte facultative sur les valeurs retournées par l'opération.                                                                                                                                                       |
|   **Visibilité**    |    Public    |                  Les valeurs autorisées et les caractères qui apparaissent dans la signature sont :<br /><br /> **+ Public** - visible globalement<br /><br /> **- Privé** : non visible en dehors du type propriétaire<br /><br /> **# Protégé** : visible pour les types dérivés du propriétaire<br /><br /> **~ Package** : visible pour d’autres types au sein du même package                   |
|    **Signature**    |  *nom*de l' + ()   |                                                                                      Résume la visibilité, le nom, les paramètres et le type de retour de cette opération. Vous pouvez modifier ces propriétés en modifiant la signature dans le diagramme ou en modifiant chaque propriété.                                                                                      |
|   **Éléments de travail**    | {0} associé |                                                                                                  Nombre d’éléments de travail associés. Lecture seule.<br /><br /> Pour plus d’informations, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Concurrence**   |  Séquentiel  | **Séquentiel** -l’opération est ou sera conçue sans contrôle d’accès concurrentiel. L'appel simultané de cette opération peut provoquer des échecs.<br /><br /> **Guarded** : l’opération se bloque automatiquement jusqu’à ce que d’autres instances de celle-ci soient terminées.<br /><br /> **Simultanée** : l’opération est conçue afin que plusieurs appels à celle-ci puissent s’exécuter simultanément. |
|    **Est statique**    |    False     |                                                                                                  Si la valeur est true, cette opération est partagée entre toutes les instances de ce type.<br /><br /> Si la valeur est true, le nom de l'opération est souligné là où il apparaît dans le diagramme.                                                                                                   |
|   **Est abstrait**   |    False     |                                                                                                                                        Si la valeur est true, aucun code n'est associé à cette opération. La classe propriétaire est donc abstraite.                                                                                                                                         |
|     **Est une feuille**     |    False     |                                                                                                                                              Le concepteur souhaite que cette opération ne puisse pas être substituée dans des classes dérivées.                                                                                                                                              |
|    **Requête is**     |    False     |                                                                                                 Si la valeur est true, aucune modification significative de l'état du système n'est effectuée par cette opération. Elle peut donc être utilisée par exemple dans un test pour vérifier l'état du système.                                                                                                  |
|  **Multiplicité**   |      1       |                                 **1** -valeur unique du type spécifié.<br /><br /> **0.. 1** -peut être `null`.<br /><br /> \* : collection de valeurs du type spécifié.<br /><br /> **1.. \\** \*-une collection contenant au moins une valeur.<br /><br /> *n* `..` *m* : collection qui contient entre `n` et les valeurs de `m`.                                  |
|   **Est ordonné**    |    False     |                                                                                                                                             Si la valeur est true, la collection forme une liste séquentielle. Pour une **multiplicité** supérieure à 1.                                                                                                                                              |
|    **Est unique**    |    False     |                                                                                                                                         Si la valeur est true, la collection ne contient pas de valeur en double. Pour une **multiplicité** supérieure à 1.                                                                                                                                         |

## <a name="see-also"></a>Voir aussi
 [Diagrammes de classes UML : référencer](../modeling/uml-class-diagrams-reference.md) [des propriétés de types dans des diagrammes de classes UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [propriétés d’attributs sur des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [propriétés d’associations dans des diagrammes de classes UML](../modeling/properties-of-associations-on-uml-class-diagrams.md) [diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)
