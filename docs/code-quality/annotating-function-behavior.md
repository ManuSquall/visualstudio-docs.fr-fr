---
title: Annotation du comportement d’une fonction
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _On_failure_
- _Return_type_success_
- _Always_
- _Maybe_raises_SEH_exception_
- _Raises_SEH_exception_
- _Called_from_function_class_
- _Function_class_
- _Must_inspect_result_
- _Success_
- _Check_return_
- _Use_decl_annotations_
ms.assetid: c0aa268d-6fa3-4ced-a8c6-f7652b152e61
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 49631248d049db5fa74bed1562e348dde15c0acc
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="annotating-function-behavior"></a>Annotation du comportement d’une fonction
En plus d’annoter [paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md), vous pouvez annoter les propriétés de la fonction entière.

## <a name="function-annotations"></a>Annotations (fonction)
 Les annotations suivantes s'appliquent à la fonction dans son ensemble, et décrivent comment elle se comporte ou ce qu'elle suppose être vrai.

|Annotation|Description|
|----------------|-----------------|
|`_Called_from_function_class_(name)`|Non destinée à une utilisation autonome ; il s'agit plutôt d'un prédicat à utiliser avec l'annotation `_When_`. Pour plus d’informations, consultez [spécifiant quand et où une Annotation est applicable](../code-quality/specifying-when-and-where-an-annotation-applies.md).<br /><br /> Le `name` paramètre est une chaîne arbitraire qui apparaît également dans un `_Function_class_` annotation dans la déclaration de certaines fonctions.  `_Called_from_function_class_` retourne zéro si la fonction qui est en cours d’analyse est annotée à l’aide de `_Function_class_` qui a la même valeur de `name`; sinon, elle retourne zéro.|
|`_Check_return_`|Annote une valeur de retour et indique que l’appelant doit l’inspecter. Le vérificateur signale une erreur si la fonction est appelée dans un contexte void.|
|`_Function_class_(name)`|Le paramètre `name` est une chaîne arbitraire indiquée par l'utilisateur.  Il existe dans un espace de noms distinct des autres espaces de noms. Une fonction, un pointeur de fonction ou, plus utilement, un type de pointeur de fonction peut être désigné comme appartenant à une ou plusieurs classes de fonction.|
|`_Raises_SEH_exception_`|Annote une fonction qui déclenche toujours une exception SEH, soumise aux conditions `_When_` et `_On_failure_`. Pour plus d’informations, consultez [spécifiant quand et où une Annotation est applicable](../code-quality/specifying-when-and-where-an-annotation-applies.md).|
|`_Maybe_raises_SEH_exception_`|Annote une fonction qui peut éventuellement déclencher une exception SEH, soumise aux conditions `_When_` et `_On_failure_`.|
|`_Must_inspect_result_`|Annote une valeur de sortie, y compris la valeur de retour, les paramètres et les variables globales.  L'analyseur signale une erreur si la valeur de l'objet annoté n'est pas ensuite inspectée. L'inspection indique si elle est utilisée dans une expression conditionnelle, est affectée à un paramètre de sortie ou un paramètre global ou est passée comme paramètre.  Pour les valeurs de retournés, `_Must_inspect_result_` implique `_Check_return_`.|
|`_Use_decl_annotations_`|Peut être utilisé à la place de la liste des annotations dans l’en-tête sur une définition de fonction (également appelé un corps de fonction).  Lorsque `_Use_decl_annotations_` est utilisé, les annotations qui apparaissent sur un en-tête dans la portée pour la même fonction sont utilisées comme s’ils sont également présents dans la définition a la `_Use_decl_annotations_` annotation.|

## <a name="successfailure-annotations"></a>Annotations de réussite/échec
 Une fonction peut échouer, et lorsque cela arrive, ses résultats peuvent être incomplets ou différer du résultat attendu.  Les annotations de la liste suivante fournissent des méthodes pour exprimer le comportement d'échec.  Pour utiliser ces annotations, vous devez leur permettre de déterminer la réussite ; une annotation `_Success_` est donc requise.  Notez que `NTSTATUS` et `HRESULT` intègrent déjà une annotation `_Success_`. Toutefois, si vous spécifiez votre propre annotation `_Success_` sur `NTSTATUS` ou `HRESULT`, celle-ci remplace l'annotation intégrée.

|Annotation|Description|
|----------------|-----------------|
|`_Always_(anno_list)`|Équivalente à `anno_list _On_failure_(anno_list)` ; en d'autres termes, les annotations dans `anno_list` s'appliquent, indépendamment de la réussite ou de l'échec de la fonction.|
|`_On_failure_(anno_list)`|À utiliser uniquement lorsque l'annotation `_Success_` est également utilisée pour annoter la fonction, explicitement ou implicitement via `_Return_type_success_` sur un typedef. Lorsque l'annotation `_On_failure_` est présente sur un paramètre de fonction ou une valeur de retour, chaque annotation dans `anno_list` (anno) se comporte comme si elle était codée en tant que `_When_(!expr, anno)`, où `expr` est le paramètre de l'annotation requise `_Success_`. Cela signifie que l'application implicite de `_Success_` à toutes les post-conditions n'est pas applicable à `_On_failure_`.|
|`_Return_type_success_(expr)`|Peut être appliquée à un typedef. Indique que toutes les fonctions qui retournent ce type et n'ont pas explicitement l'annotation `_Success_` sont annotées comme si elles avaient l'annotation `_Success_(expr)`. L'annotation `_Return_type_success_` ne peut pas être utilisée sur un typedef de fonction ou de pointeur de fonction.|
|`_Success_(expr)`|`expr` est une expression qui retourne une valeur rvalue. Lorsque l'annotation `_Success_` est présente dans une déclaration ou une définition de fonction, chaque annotation (`anno`) sur la fonction et dans la condition préalable se comporte comme si elle était codée en tant que `_When_(expr, anno)`. L'annotation `_Success_` peut uniquement être utilisée sur une fonction, et non sur ses paramètres ou son type de retour. Il peut y avoir au plus une annotation `_Success_` sur une fonction, et elle ne peut pas être dans `_When_`, `_At_` ou `_Group_`. Pour plus d’informations, consultez [spécifiant quand et où une Annotation est applicable](../code-quality/specifying-when-and-where-an-annotation-applies.md).|

## <a name="see-also"></a>Voir aussi
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md) [présentation de SAL](../code-quality/understanding-sal.md) [annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md) [Structs et Classesd’annotation](../code-quality/annotating-structs-and-classes.md) [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md) [spécifiant le moment où une Annotation est applicable et](../code-quality/specifying-when-and-where-an-annotation-applies.md) [des fonctions intrinsèques](../code-quality/intrinsic-functions.md) [meilleures pratiques et Exemples](../code-quality/best-practices-and-examples-sal.md)