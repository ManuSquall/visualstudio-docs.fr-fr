---
title: "Annotation de paramètres de fonction et valeurs de retour | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ac25f8bbda4431850f613f2b41b1d9ed4908c118
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="annotating-function-parameters-and-return-values"></a>Annotation de paramètres de fonction et valeurs de retour
Cet article décrit les utilisations courantes des annotations pour les paramètres de fonction simple, les scalaires et les pointeurs vers des structures et des classes et la plupart des types de mémoires tampons.  Cet article présente également des modèles d’utilisation courants pour les annotations. Pour les annotations supplémentaires qui sont liées à des fonctions, consultez [annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>Paramètres de pointeur  
 Pour les annotations dans le tableau suivant, un paramètre de pointeur est annoté, l’analyseur signale une erreur si le pointeur est null.  Cela s’applique aux pointeurs et des éléments de données vers laquelle pointe.  
  
 **Annotations et Descriptions**  
  
-   `_In_`  
  
     Annote les paramètres d’entrée qui sont des valeurs scalaires, structures, des pointeurs vers des structures et autres.  Explicitement peuvent être utilisés sur des valeurs scalaires simples.  Le paramètre doit être valide dans l’état préliminaire et ne sera pas modifié.  
  
-   `_Out_`  
  
     Annote les paramètres de sortie qui sont des valeurs scalaires, structures, des pointeurs vers des structures et autres.  Ne s’appliquent pas cela à un objet qui ne peut pas retourner une valeur, par exemple, une valeur scalaire qui est passée par valeur.  Le paramètre pas nécessairement être valide dans l’état préalable mais doit être valide dans l’état postérieur à.  
  
-   `_Inout_`  
  
     Annote un paramètre qui est modifié par la fonction.  Il doit être valide en état avant et après, mais il est supposé pour avoir des valeurs différentes avant et après l’appel. Doit s’appliquent à une valeur modifiable.  
  
-   `_In_z_`  
  
     Pointeur vers une chaîne se terminant par null qui est utilisé comme entrée.  La chaîne doit être valide dans l’état préalable.  Variantes de `PSTR`, lequel déjà ont les annotations correctes, par défaut.  
  
-   `_Inout_z_`  
  
     Pointeur vers un tableau de caractères terminée par une valeur null sera modifié.  Il doit être valide avant et après l’appel, mais la valeur est supposée avoir été modifié.  Le terminateur null peut-être être déplacé, mais uniquement les éléments jusqu'à la marque de fin null d’origine est accessible.  
  
-   `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Pointeur vers un tableau, qui est lu par la fonction.  Le tableau est de taille `s` éléments, qui doit être valide.  
  
     Le `_bytes_` variante donne la taille en octets au lieu d’éléments. Utilisez cette option uniquement lorsque la taille ne peut pas être exprimée sous forme d’éléments.  Par exemple, `char` chaînes utiliserait la `_bytes_` variante uniquement si la fonctionnent similaires qui utilise `wchar_t` serait.  
  
-   `_In_reads_z_(s)`  
  
     Pointeur vers un tableau qui se termine par null et a une taille connue. Les éléments jusqu'à la marque de fin null, ou `s` s’il n’existe aucune marque de fin null, doit être valide dans l’état préalable.  Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  
  
-   `_In_reads_or_z_(s)`  
  
     Pointeur vers un tableau qui est terminée ou a une taille connue, ou les deux. Les éléments jusqu'à la marque de fin null, ou `s` s’il n’existe aucune marque de fin null, doit être valide dans l’état préalable.  Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  (Utilisé pour le `strn` famille.)  
  
-   `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Un pointeur vers un tableau de `s` éléments (octets gestion) qui seront écrits par la fonction.  Les éléments du tableau n’ont pas à être valide dans l’état avant, et le nombre d’éléments qui sont valides dans l’état postérieur à n’est pas spécifié.  S’il existe des annotations sur le type de paramètre, elles sont appliquées dans l’état postérieur à. Par exemple, prenons le code suivant.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     Dans cet exemple, l’appelant fournit une mémoire tampon de `size` éléments pour `p1`.  `MyStringCopy`certains de ces éléments, valide. Plus important encore, la `_Null_terminated_` annotation sur `PWSTR` signifie que `p1` est terminée par null dans l’état postérieur à.  De cette façon, le nombre d’éléments valides est toujours bien défini, mais un nombre d’éléments spécifique n’est pas requis.  
  
     Le `_bytes_` variante donne la taille en octets au lieu d’éléments. Utilisez cette option uniquement lorsque la taille ne peut pas être exprimée sous forme d’éléments.  Par exemple, `char` chaînes utiliserait la `_bytes_` variante uniquement si la fonctionnent similaires qui utilise `wchar_t` serait.  
  
-   `_Out_writes_z_(s)`  
  
     Un pointeur vers un tableau de `s` éléments.  Les éléments n’ont pas soit valide dans l’état préalable.  Dans l’état postérieur à, les éléments de configuration via le terminateur null, qui doit être présent, doit être valide.  Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  
  
-   `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Pointeur vers un tableau, qui est à la fois lues et écrit dans la fonction.  Il est de taille `s` éléments et valide dans l’état d’avant et après.  
  
     Le `_bytes_` variante donne la taille en octets au lieu d’éléments. Utilisez cette option uniquement lorsque la taille ne peut pas être exprimée sous forme d’éléments.  Par exemple, `char` chaînes utiliserait la `_bytes_` variante uniquement si la fonctionnent similaires qui utilise `wchar_t` serait.  
  
-   `_Inout_updates_z_(s)`  
  
     Pointeur vers un tableau qui se termine par null et a une taille connue. Les éléments de configuration via le terminateur null, qui doit être présent, doit être valide à la fois état avant ou après.  La valeur dans l’état postérieur est censée être différente de la valeur dans l’état préliminaire ; Cela inclut l’emplacement de la marque de fin null. Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Un pointeur vers un tableau de `s` éléments.  Les éléments n’ont pas soit valide dans l’état préalable.  Dans l’état postérieur à, les éléments du `c`- ième élément doit être valide.  Si la taille est connue en octets, à l’échelle `s` et `c` par la taille de l’élément ou l’utilisation du `_bytes_` variant, ce qui est défini comme :  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     En d’autres termes, chaque élément qui existe dans la mémoire tampon jusqu'à `s` dans l’état préliminaire est valide dans l’état postérieur à.  Exemple :  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Pointeur vers un tableau, qui est lue et modifiée par la fonction.  Il est de taille `s` éléments, qui doit être valide dans l’état préalable, et `c` éléments doivent être valides dans l’état postérieur à.  
  
     Le `_bytes_` variante donne la taille en octets au lieu d’éléments. Utilisez cette option uniquement lorsque la taille ne peut pas être exprimée sous forme d’éléments.  Par exemple, `char` chaînes utiliserait la `_bytes_` variante uniquement si la fonctionnent similaires qui utilise `wchar_t` serait.  
  
-   `_Inout_updates_z_(s)`  
  
     Pointeur vers un tableau qui se termine par null et a une taille connue. Les éléments de configuration via le terminateur null, qui doit être présent, doit être valide à la fois état avant ou après.  La valeur dans l’état postérieur est censée être différente de la valeur dans l’état préliminaire ; Cela inclut l’emplacement de la marque de fin null. Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Un pointeur vers un tableau de `s` éléments.  Les éléments n’ont pas soit valide dans l’état préalable.  Dans l’état postérieur à, les éléments du `c`- ième élément doit être valide.  Si la taille est connue en octets, à l’échelle `s` et `c` par la taille de l’élément ou l’utilisation du `_bytes_` variant, ce qui est défini comme :  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     En d’autres termes, chaque élément qui existe dans la mémoire tampon jusqu'à `s` dans l’état préliminaire est valide dans l’état postérieur à.  Exemple :  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Pointeur vers un tableau, qui est lue et modifiée par la fonction.  Il est de taille `s` éléments, qui doit être valide dans l’état préalable, et `c` éléments doivent être valides dans l’état postérieur à.  
  
     Le `_bytes_` variante donne la taille en octets au lieu d’éléments. Utilisez cette option uniquement lorsque la taille ne peut pas être exprimée sous forme d’éléments.  Par exemple, `char` chaînes utiliserait la `_bytes_` variante uniquement si la fonctionnent similaires qui utilise `wchar_t` serait.  
  
-   `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Un pointeur vers un tableau, qui est lue et modifiée par la fonction de la taille `s` éléments. Défini comme étant équivalent à :  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     En d’autres termes, chaque élément qui existe dans la mémoire tampon jusqu'à `s` dans l’état préliminaire est valide l’état avant ou après.  
  
     Le `_bytes_` variante donne la taille en octets au lieu d’éléments. Utilisez cette option uniquement lorsque la taille ne peut pas être exprimée sous forme d’éléments.  Par exemple, `char` chaînes utiliserait la `_bytes_` variante uniquement si la fonctionnent similaires qui utilise `wchar_t` serait.  
  
-   `_In_reads_to_ptr_(p)`  
  
     Un pointeur vers un tableau pour lequel l’expression `p`  -  `_Curr_` (autrement dit, `p` moins `_Curr_`) est défini par la norme du langage approprié.  Les éléments antérieurs à `p` doit être valide dans l’état préalable.  
  
-   `_In_reads_to_ptr_z_(p)`  
  
     Un pointeur vers un tableau se terminant par null pour lesquelles l’expression `p`  -  `_Curr_` (autrement dit, `p` moins `_Curr_`) est défini par la norme du langage approprié.  Les éléments antérieurs à `p` doit être valide dans l’état préalable.  
  
-   `_Out_writes_to_ptr_(p)`  
  
     Un pointeur vers un tableau pour lequel l’expression `p`  -  `_Curr_` (autrement dit, `p` moins `_Curr_`) est défini par la norme du langage approprié.  Les éléments antérieurs à `p` n’avez pas à être valide dans l’état préliminaire et doit être valide dans l’état postérieur à.  
  
-   `_Out_writes_to_ptr_z_(p)`  
  
     Un pointeur vers un tableau se terminant par null pour lesquelles l’expression `p`  -  `_Curr_` (autrement dit, `p` moins `_Curr_`) est défini par la norme du langage approprié.  Les éléments antérieurs à `p` n’avez pas à être valide dans l’état préliminaire et doit être valide dans l’état postérieur à.  
  
## <a name="optional-pointer-parameters"></a>Paramètres de pointeur facultatif  
 Lorsqu’une annotation de paramètre pointeur inclut `_opt_`, il indique que le paramètre peut être null. Sinon, l’annotation effectue la même que la version qui n’inclut pas `_opt_`. Voici une liste de la `_opt_` variantes des annotations de paramètre de pointeur :  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Paramètres de pointeur de sortie  
 Paramètres de pointeur de sortie requièrent une notation spéciale pour lever l’ambiguïté de nature null sur le paramètre et l’emplacement désigné.  
  
 **Annotations et Descriptions**  
  
-   `_Outptr_`  
  
     Le paramètre ne peut pas être null et l’état postérieur à l’emplacement désigné ne peut pas être null et doit être valide.  
  
-   `_Outptr_opt_`  
  
     Paramètre peut être null, mais l’état postérieur à l’emplacement désigné ne peut pas être null et doit être valide.  
  
-   `_Outptr_result_maybenull_`  
  
     Le paramètre ne peut pas être null, et dans l’état postérieur à l’emplacement désigné peut être null.  
  
-   `_Outptr_opt_result_maybenull_`  
  
     Paramètre peut être null, et dans l’état postérieur à l’emplacement désigné peut être null.  
  
 Dans le tableau suivant, les sous-chaînes supplémentaires sont insérées dans le nom de l’annotation pour qualifier davantage la signification de l’annotation.  Les sous-chaînes différents sont `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, et `_to_`.  
  
> [!IMPORTANT]
>  Si l’interface que vous annotez est COM, utilisez la forme COM de ces annotations. N’utilisez pas les annotations COM avec toute autre interface de type.  
  
 **Annotations et Descriptions**  
  
-   `_Outptr_result_z_`  
  
     `_Outptr_opt_result_z_`  
  
     `_Outptr_result_maybenull_z_`  
  
     `_Ouptr_opt_result_maybenull_z_`  
  
     Le pointeur retourné a le `_Null_terminated_` annotation.  
  
-   `_COM_Outptr_`  
  
     `_COM_Outptr_opt_`  
  
     `_COM_Outptr_result_maybenull_`  
  
     `_COM_Outptr_opt_result_maybenull_`  
  
     Le pointeur retourné a une sémantique COM et par conséquent comporte un `_On_failure_` à condition que le pointeur retourné est null.  
  
-   `_Outptr_result_buffer_(s)`  
  
     `_Outptr_result_bytebuffer_(s)`  
  
     `_Outptr_opt_result_buffer_(s)`  
  
     `_Outptr_opt_result_bytebuffer_(s)`  
  
     Le pointeur retourné pointe vers la mémoire tampon de taille valide `s` éléments ou octets.  
  
-   `_Outptr_result_buffer_to_(s, c)`  
  
     `_Outptr_result_bytebuffer_to_(s, c)`  
  
     `_Outptr_opt_result_buffer_to_(s,c)`  
  
     `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
     Le pointeur retourné pointe vers une mémoire tampon de taille `s` éléments ou octets dont la première `c` sont valides.  
  
 Certaines conventions interface présument que les paramètres de sortie sont annulés en cas d’échec.  À l’exception du code explicitement COM, les formulaires dans le tableau suivant sont préférables.  Pour le code COM, utilisez les formats COM correspondants qui sont répertoriés dans la section précédente.  
  
 **Annotations et Descriptions**  
  
-   `_Result_nullonfailure_`  
  
     Modifie les autres annotations. Le résultat a la valeur null si la fonction échoue.  
  
-   `_Result_zeroonfailure_`  
  
     Modifie les autres annotations. Le résultat est la valeur zéro si la fonction échoue.  
  
-   `_Outptr_result_nullonfailure_`  
  
     Le pointeur retourné pointe vers une mémoire tampon valides si la fonction réussit, ou null si la fonction échoue. Cette annotation est pour un paramètre obligatoire.  
  
-   `_Outptr_opt_result_nullonfailure_`  
  
     Le pointeur retourné pointe vers une mémoire tampon valides si la fonction réussit, ou null si la fonction échoue. Cette annotation est pour un paramètre optionnel.  
  
-   `_Outref_result_nullonfailure_`  
  
     Le pointeur retourné pointe vers une mémoire tampon valides si la fonction réussit, ou null si la fonction échoue. Cette annotation est pour un paramètre de référence.  
  
## <a name="output-reference-parameters"></a>Paramètres de référence de sortie  
 Une utilisation courante de paramètre de référence est pour les paramètres output.  Pour les paramètres de référence de sortie simple, par exemple, `int&`:`_Out_` fournit la sémantique appropriée.  Toutefois, lorsque la valeur de sortie est un pointeur, par exemple `int *&`: les annotations équivalentes pointeur comme `_Outptr_ int **` ne fournissent pas la sémantique appropriée.  Pour concise exprimer la sémantique de référence des paramètres de sortie pour les types pointeur, utilisez ces annotations composites :  
  
 **Annotations et Descriptions**  
  
-   `_Outref_`  
  
     Résultat doit être valide dans l’état postérieur à et ne peut pas être null.  
  
-   `_Outref_result_maybenull_`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état postérieur à.  
  
-   `_Outref_result_buffer_(s)`  
  
     Résultat doit être valide dans l’état postérieur à et ne peut pas être null. Pointe vers une mémoire tampon valide de taille `s` éléments.  
  
-   `_Outref_result_bytebuffer_(s)`  
  
     Résultat doit être valide dans l’état postérieur à et ne peut pas être null. Pointe vers une mémoire tampon valide de taille `s` octets.  
  
-   `_Outref_result_buffer_to_(s, c)`  
  
     Résultat doit être valide dans l’état postérieur à et ne peut pas être null. Pointe vers une mémoire tampon de `s` éléments, dont la première `c` sont valides.  
  
-   `_Outref_result_bytebuffer_to_(s, c)`  
  
     Résultat doit être valide dans l’état postérieur à et ne peut pas être null. Pointe vers une mémoire tampon de `s` octets dont la première `c` sont valides.  
  
-   `_Outref_result_buffer_all_(s)`  
  
     Résultat doit être valide dans l’état postérieur à et ne peut pas être null. Pointe vers une mémoire tampon valide de taille `s` éléments valides.  
  
-   `_Outref_result_bytebuffer_all_(s)`  
  
     Résultat doit être valide dans l’état postérieur à et ne peut pas être null. Pointe vers une mémoire tampon valides de `s` octets d’éléments valides.  
  
-   `_Outref_result_buffer_maybenull_(s)`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état postérieur à. Pointe vers une mémoire tampon valide de taille `s` éléments.  
  
-   `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état postérieur à. Pointe vers une mémoire tampon valide de taille `s` octets.  
  
-   `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état postérieur à. Pointe vers une mémoire tampon de `s` éléments, dont la première `c` sont valides.  
  
-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état de la publication. Pointe vers une mémoire tampon de `s` octets dont la première `c` sont valides.  
  
-   `_Outref_result_buffer_all_maybenull_(s)`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état de la publication. Pointe vers une mémoire tampon valide de taille `s` éléments valides.  
  
-   `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état de la publication. Pointe vers une mémoire tampon valides de `s` octets d’éléments valides.  
  
## <a name="return-values"></a>Valeurs de retour  
 La valeur de retour d’une fonction ressemble à un `_Out_` paramètre, mais est à différents niveaux de de-reference, et vous n’êtes pas obligé de prendre en compte le concept d’un pointeur vers le résultat.  Pour les annotations suivantes, la valeur de retour est l’objet annoté : une valeur scalaire, un pointeur vers une structure ou un pointeur vers une mémoire tampon. Ces annotations ont la même sémantique correspondants `_Out_` annotation.  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>Autres Annotations courantes  
 **Annotations et Descriptions**  
  
-   `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Le paramètre, le champ ou le résultat est dans la plage (incluse) à partir de `low` à `hi`.  Équivalent à `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` qui est appliqué à l’objet annoté ainsi que les conditions d’états avant ou après l’état appropriées.  
  
    > [!IMPORTANT]
    >  Bien que les noms contiennent « in » et « sortie », la sémantique de `_In_` et `_Out_` faire **pas** s’appliquent à ces annotations.  
  
-   `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     La valeur annotée est exactement `expr`.  Équivalent à `_Satisfies_(_Curr_ == expr)` qui est appliqué à l’objet annoté ainsi que les conditions d’états avant ou après l’état appropriées.  
  
-   `_Struct_size_bytes_(size)`  
  
     S’applique à une déclaration de classe ou de struct.  Indique qu’un objet valide de ce type peut être plus grand que le type déclaré, le nombre d’octets qui est fourni par `size`.  Exemple :  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     La taille de mémoire tampon en octets d’un paramètre `pM` de type `MyStruct *` est ensuite dirigé vers l’être :  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Ressources connexes  
 [Blog de l’équipe analyse du code](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Les structures et Classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécification de quand et où une Annotation est applicable](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Meilleures pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)