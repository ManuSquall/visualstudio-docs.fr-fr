---
title: Propriétés d’opérations sur UML des diagrammes de classes | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c2392cf951c5f25a5b287a1d56338b03bebb27e0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207023"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Propriétés d'opérations dans des diagrammes de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sur un diagramme de classes UML, vous pouvez ajouter *opérations* aux classes et interfaces. Une opération est une méthode ou une fonction qui peut être exécutée par une instance d'une classe ou d'une interface.  
  
 Pour ajouter une opération, avec le bouton droit de la classe ou interface, pointez sur **ajouter**, puis cliquez sur **opération**.  
  
 Si les opérations d'une classe ne sont pas visibles dans le diagramme, cliquez sur le chevron de développement situé en haut de la classe ou de l'interface. Si vous pouvez voir le **opération** en-tête, cliquez sur **[+]** pour développer la section opérations.  
  
## <a name="signature-of-an-operation"></a>Signature d'une opération  
 La signature d'une opération est la ligne de texte qui le représente dans une classe ou une interface dans un diagramme de classes UML. Son format est le suivant :  
  
 \+ OperationName (parameter1 : Type1 [*],...) : ReturnType [\*]  
  
 \+ Indique une visibilité publique. Les autres valeurs autorisées sont - (privé), # (protégé), ~ (package).  
  
 `OperationName` est souligné si le **Is Static** propriété a la valeur true et est en italique si le **Is Abstract** propriété a la valeur true.  
  
 `: ReturnType` est omis si aucun type de retour n'est défini.  
  
 `[*]` indique la multiplicité d'un paramètre ou d'un type de retour. Il est omis si la multiplicité est 1.  
  
 Pour obtenir une description complète de ces propriétés, consultez la section suivante.  
  
## <a name="properties"></a>Propriétés  
 Il s'agit des propriétés d'une opération dans une classe ou une interface dans un diagramme de classes UML.  
  
 Pour afficher les propriétés d’une opération, avec le bouton droit de l’opération dans la classe ou interface sur le diagramme, puis cliquez sur **propriétés**. Les propriétés s’affichent dans le **propriétés** fenêtre.  
  
|Propriété|Par défaut|Description|  
|--------------|-------------|-----------------|  
|**Name**|(un nouveau nom)|Doit être unique dans le type conteneur.|  
|**Paramètres**|(aucune)|Une liste qui se présente sous la forme _nom_**:**_Type_**,** _nom_**:**  _Type_**,...** Cliquez sur **[...]**  pour modifier la liste.<br /><br /> Les types peuvent être des types primitifs ou des types définis dans le modèle. Si vous entrez un nom pour un nouveau type dans cette propriété, un type est ajouté à la section **Types non spécifiés** de l’Explorateur de modèles UML.|  
|**Type de retour**|(aucune)|**(aucun)** , ou un type primitif ou un type qui est défini dans le modèle. Si vous entrez un nom pour un nouveau type dans cette propriété, un type est ajouté à la section **Types non spécifiés** de l’Explorateur de modèles UML.|  
|**Post-conditions**|(aucune)|Condition facultative spécifiant une relation entre l'état du système avant et après l'exécution de l'opération.|  
|**Conditions préalables**|(aucune)|Condition facultative spécifiant les hypothèses concernant l'état du système avant l'exécution de l'opération.|  
|**Conditions de corps**|(aucune)|Contrainte facultative sur les valeurs retournées par l'opération.|  
|**Visibilité**|Public|Les valeurs autorisées et les caractères qui apparaissent dans la signature sont :<br /><br /> **+ Public** - visible globalement<br /><br /> **- Privé** : non visible en dehors du type propriétaire<br /><br /> **# Protégé** : visible pour les types dérivés du propriétaire<br /><br /> **~ Package** : visible pour d’autres types au sein du même package|  
|**Signature**|+*Nom*()|Résume la visibilité, le nom, les paramètres et le type de retour de cette opération. Vous pouvez modifier ces propriétés en modifiant la signature dans le diagramme ou en modifiant chaque propriété.|  
|**Éléments de travail**|{0} associé|Nombre d’éléments de travail associés. Lecture seule.<br /><br /> Pour plus d’informations, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|  
|**Concurrence**|Séquentiel|**Séquentiel** -l’opération est ou sera conçue sans contrôle d’accès concurrentiel. L'appel simultané de cette opération peut provoquer des échecs.<br /><br /> **Service Guardian** -l’opération est bloquée automatiquement jusqu'à ce que les autres instances terminées.<br /><br /> **Simultanées** -l’opération est conçue afin que plusieurs appels puissent se pouvant s’exécuter simultanément.|  
|**Est statique**|False|Si la valeur est true, cette opération est partagée entre toutes les instances de ce type.<br /><br /> Si la valeur est true, le nom de l'opération est souligné là où il apparaît dans le diagramme.|  
|**Est abstrait**|False|Si la valeur est true, aucun code n'est associé à cette opération. La classe propriétaire est donc abstraite.|  
|**Est une feuille**|False|Le concepteur souhaite que cette opération ne puisse pas être substituée dans des classes dérivées.|  
|**Est la requête**|False|Si la valeur est true, aucune modification significative de l'état du système n'est effectuée par cette opération. Elle peut donc être utilisée par exemple dans un test pour vérifier l'état du système.|  
|**Multiplicité**|1|**1** -une valeur unique du type spécifié.<br /><br /> **valeur 0.. 1** -peut être `null`.<br /><br /> \* -une collection de valeurs du type spécifié.<br /><br /> **1..\***  - collection contenant au moins une valeur.<br /><br /> *n* `..` *m* -une collection qui contient entre `n` et `m` valeurs.|  
|**Est ordonné**|False|Si la valeur est true, la collection forme une liste séquentielle. Pour **multiplicité** plus de 1.|  
|**Est Unique**|False|Si la valeur est true, la collection ne contient pas de valeur en double. Pour **multiplicité** plus de 1.|  
  
## <a name="see-also"></a>Voir aussi  
 [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)   
 [Propriétés de types de diagrammes de classes UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Propriétés d’attributs dans des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Propriétés des associations dans des diagrammes de classes UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [Diagrammes de classes UML : recommandations](../modeling/uml-class-diagrams-guidelines.md)



