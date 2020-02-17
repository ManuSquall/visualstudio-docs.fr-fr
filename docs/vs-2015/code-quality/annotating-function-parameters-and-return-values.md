---
title: Annotation des paramètres de fonction et des valeurs de retour | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
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
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: bd9107bed68b9b5b6f88a239b3b155440b0e654c
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271614"
---
# <a name="annotating-function-parameters-and-return-values"></a>Annotation de paramètres de fonction et valeurs de retour
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cet article décrit les utilisations typiques des annotations pour les paramètres de fonction simples (scalaires et pointeurs vers les structures et les classes) et la plupart des types de mémoires tampons.  Cet article présente également les modèles d’utilisation courants pour les annotations. Pour des annotations supplémentaires liées aux fonctions, consultez [annotation du comportement](../code-quality/annotating-function-behavior.md) des fonctions  
  
## <a name="pointer-parameters"></a>Paramètres du pointeur  
 Pour les annotations dans le tableau suivant, quand un paramètre de pointeur est annoté, l’analyseur signale une erreur si le pointeur est null.  Cela s’applique aux pointeurs et à tout élément de données vers lequel pointe.  
  
 **Annotations et descriptions**  
  
- `_In_`  
  
     Annote des paramètres d’entrée qui sont des valeurs scalaires, des structures, des pointeurs vers des structures et autres.  Peut être utilisé explicitement sur des scalaires simples.  Le paramètre doit être valide dans un état antérieur et ne sera pas modifié.  
  
- `_Out_`  
  
     Annote les paramètres de sortie qui sont des scalaires, des structures, des pointeurs vers des structures et autres.  Ne l’appliquez pas à un objet qui ne peut pas retourner une valeur (par exemple, un scalaire passé par valeur).  Le paramètre ne doit pas nécessairement être valide dans un état antérieur, mais doit être valide dans le billet.  
  
- `_Inout_`  
  
     Annote un paramètre qui sera modifié par la fonction.  Elle doit être valide à la fois à l’état antérieur et postérieur, mais elle est supposée avoir des valeurs différentes avant et après l’appel. Doit s’appliquer à une valeur modifiable.  
  
- `_In_z_`  
  
     Pointeur vers une chaîne terminée par le caractère null qui est utilisée comme entrée.  La chaîne doit être valide dans un état antérieur.  Les variantes de `PSTR`, qui ont déjà les annotations correctes, sont préférées.  
  
- `_Inout_z_`  
  
     Pointeur vers un tableau de caractères se terminant par un caractère null qui sera modifié.  Elle doit être valide avant et après l’appel, mais la valeur est supposée avoir changé.  La marque de fin null peut être déplacée, mais seuls les éléments jusqu’à la marque de fin null d’origine sont accessibles.  
  
- `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Pointeur vers un tableau, qui est lu par la fonction.  Le tableau est de taille `s` éléments, qui doivent tous être valides.  
  
     Le `_bytes_` variant donne la taille en octets au lieu des éléments. À utiliser uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, les chaînes de `char` utilisent le variant `_bytes_` uniquement si une fonction similaire qui utilise `wchar_t`.  
  
- `_In_reads_z_(s)`  
  
     Pointeur vers un tableau qui se termine par un caractère null et a une taille connue. Les éléments jusqu’au terminateur null, ou `s` s’il n’y a pas de marque de fin null, doivent être valides dans un état antérieur.  Si la taille est connue en octets, mettez à l’échelle `s` par la taille de l’élément.  
  
- `_In_reads_or_z_(s)`  
  
     Pointeur vers un tableau qui se termine par un caractère null ou qui a une taille connue, ou les deux. Les éléments jusqu’au terminateur null, ou `s` s’il n’y a pas de marque de fin null, doivent être valides dans un état antérieur.  Si la taille est connue en octets, mettez à l’échelle `s` par la taille de l’élément.  (Utilisé pour la famille de `strn`.)  
  
- `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Pointeur vers un tableau d’éléments `s` (resp. octets) qui sera écrit par la fonction.  Les éléments de tableau ne doivent pas nécessairement être valides dans un état antérieur, et le nombre d’éléments valides dans le billet n’est pas spécifié.  S’il existe des annotations sur le type de paramètre, elles sont appliquées à l’État postérieur. Par exemple, prenons le code suivant.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     Dans cet exemple, l’appelant fournit une mémoire tampon d’éléments `size` pour `p1`.  `MyStringCopy` rend certains de ces éléments valides. Plus important encore, l’annotation `_Null_terminated_` sur `PWSTR` signifie que `p1` se termine par un caractère NULL dans un État postérieur.  De cette façon, le nombre d’éléments valides est toujours bien défini, mais un nombre d’éléments spécifique n’est pas requis.  
  
     Le `_bytes_` variant donne la taille en octets au lieu des éléments. À utiliser uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, les chaînes de `char` utilisent le variant `_bytes_` uniquement si une fonction similaire qui utilise `wchar_t`.  
  
- `_Out_writes_z_(s)`  
  
     Pointeur vers un tableau d’éléments `s`.  Les éléments ne doivent pas nécessairement être valides dans un état antérieur.  Dans un État postérieur, les éléments au-dessus de la marque de fin null (qui doit être présent) doivent être valides.  Si la taille est connue en octets, mettez à l’échelle `s` par la taille de l’élément.  
  
- `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Pointeur vers un tableau, qui est à la fois lu et écrit dans la fonction.  Elle est de taille `s` éléments et est valide dans un état antérieur et postérieur.  
  
     Le `_bytes_` variant donne la taille en octets au lieu des éléments. À utiliser uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, les chaînes de `char` utilisent le variant `_bytes_` uniquement si une fonction similaire qui utilise `wchar_t`.  
  
- `_Inout_updates_z_(s)`  
  
     Pointeur vers un tableau qui se termine par un caractère null et a une taille connue. Les éléments jusqu’au terminateur null (qui doit être présent) doivent être valides à la fois dans l’état antérieur et après l’État.  La valeur de l’État postérieur est supposée être différente de la valeur de l’état antérieur ; Cela comprend l’emplacement de la marque de fin null. Si la taille est connue en octets, mettez à l’échelle `s` par la taille de l’élément.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Pointeur vers un tableau d’éléments `s`.  Les éléments ne doivent pas nécessairement être valides dans un état antérieur.  Dans un État postérieur, les éléments jusqu’au `c`-ième élément doivent être valides.  Si la taille est connue en octets, mettez à l’échelle `s` et `c` par la taille de l’élément ou utilisez la variante `_bytes_`, qui est définie comme suit :  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     En d’autres termes, tous les éléments qui existent dans la mémoire tampon jusqu’à `s` dans le pré-État sont valides dans l’État postérieur.  Par exemple :  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Pointeur vers un tableau, qui est lu et écrit par la fonction.  Elle est de taille `s` éléments, qui doivent tous être valides dans un état antérieur, et les éléments `c` doivent être valides dans un État postérieur.  
  
     Le `_bytes_` variant donne la taille en octets au lieu des éléments. À utiliser uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, les chaînes de `char` utilisent le variant `_bytes_` uniquement si une fonction similaire qui utilise `wchar_t`.  
  
- `_Inout_updates_z_(s)`  
  
     Pointeur vers un tableau qui se termine par un caractère null et a une taille connue. Les éléments jusqu’au terminateur null (qui doit être présent) doivent être valides à la fois dans l’état antérieur et après l’État.  La valeur de l’État postérieur est supposée être différente de la valeur de l’état antérieur ; Cela comprend l’emplacement de la marque de fin null. Si la taille est connue en octets, mettez à l’échelle `s` par la taille de l’élément.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Pointeur vers un tableau d’éléments `s`.  Les éléments ne doivent pas nécessairement être valides dans un état antérieur.  Dans un État postérieur, les éléments jusqu’au `c`-ième élément doivent être valides.  Si la taille est connue en octets, mettez à l’échelle `s` et `c` par la taille de l’élément ou utilisez la variante `_bytes_`, qui est définie comme suit :  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     En d’autres termes, tous les éléments qui existent dans la mémoire tampon jusqu’à `s` dans le pré-État sont valides dans l’État postérieur.  Par exemple :  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Pointeur vers un tableau, qui est lu et écrit par la fonction.  Elle est de taille `s` éléments, qui doivent tous être valides dans un état antérieur, et les éléments `c` doivent être valides dans un État postérieur.  
  
     Le `_bytes_` variant donne la taille en octets au lieu des éléments. À utiliser uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, les chaînes de `char` utilisent le variant `_bytes_` uniquement si une fonction similaire qui utilise `wchar_t`.  
  
- `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Pointeur vers un tableau, qui est lu et écrit par la fonction de taille `s` éléments. Défini comme équivalent à :  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     En d’autres termes, tous les éléments qui existent dans la mémoire tampon jusqu’à `s` dans le préétat sont valides dans l’état antérieur et postérieur.  
  
     Le `_bytes_` variant donne la taille en octets au lieu des éléments. À utiliser uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, les chaînes de `char` utilisent le variant `_bytes_` uniquement si une fonction similaire qui utilise `wchar_t`.  
  
- `_In_reads_to_ptr_(p)`  
  
     Pointeur vers un tableau pour lequel l’expression `p` – `_Curr_` (autrement dit, `p` moins `_Curr_`) est définie par la norme de langage appropriée.  Les éléments antérieurs à `p` doivent être valides dans un état antérieur.  
  
- `_In_reads_to_ptr_z_(p)`  
  
     Pointeur vers un tableau se terminant par un caractère null pour lequel l’expression `p` – `_Curr_` (autrement dit, `p` moins `_Curr_`) est définie par la norme de langage appropriée.  Les éléments antérieurs à `p` doivent être valides dans un état antérieur.  
  
- `_Out_writes_to_ptr_(p)`  
  
     Pointeur vers un tableau pour lequel l’expression `p` – `_Curr_` (autrement dit, `p` moins `_Curr_`) est définie par la norme de langage appropriée.  Les éléments antérieurs à `p` n’ont pas besoin d’être valides dans un état antérieur et doivent être valides dans un État postérieur.  
  
- `_Out_writes_to_ptr_z_(p)`  
  
     Pointeur vers un tableau se terminant par un caractère null pour lequel l’expression `p` – `_Curr_` (autrement dit, `p` moins `_Curr_`) est définie par la norme de langage appropriée.  Les éléments antérieurs à `p` n’ont pas besoin d’être valides dans un état antérieur et doivent être valides dans un État postérieur.  
  
## <a name="optional-pointer-parameters"></a>Paramètres de pointeur facultatifs  
 Quand une annotation de paramètre de pointeur comprend `_opt_`, elle indique que le paramètre peut être null. Dans le cas contraire, l’annotation est identique à la version qui n’inclut pas `_opt_`. Voici la liste des `_opt_` variantes des annotations de paramètre de pointeur :  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Paramètres du pointeur de sortie  
 Les paramètres de pointeur de sortie requièrent une notation spéciale pour lever l’ambiguïté des valeurs NULL sur le paramètre et l’emplacement pointé.  
  
 **Annotations et descriptions**  
  
- `_Outptr_`  
  
   Le paramètre ne peut pas avoir la valeur null et, dans l’État postérieur, l’emplacement pointé ne peut pas être null et doit être valide.  
  
- `_Outptr_opt_`  
  
   Le paramètre peut avoir la valeur null, mais dans l’État postérieur, l’emplacement pointé ne peut pas être null et doit être valide.  
  
- `_Outptr_result_maybenull_`  
  
   Le paramètre ne peut pas avoir la valeur null et, dans l’État postérieur, l’emplacement pointé peut avoir la valeur null.  
  
- `_Outptr_opt_result_maybenull_`  
  
   Le paramètre peut avoir la valeur null et, dans l’État postérieur, l’emplacement pointé peut avoir la valeur null.  
  
  Dans le tableau suivant, des sous-chaînes supplémentaires sont insérées dans le nom de l’annotation pour qualifier davantage la signification de l’annotation.  Les différentes sous-chaînes sont `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`et `_to_`.  
  
> [!IMPORTANT]
> Si l’interface que vous annotez est COM, utilisez la forme COM de ces annotations. N’utilisez pas les annotations COM avec une autre interface de type.  
  
 **Annotations et descriptions**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   Le pointeur retourné a l’annotation `_Null_terminated_`.  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   Le pointeur retourné a une sémantique COM et, par conséquent, transporte un `_On_failure_` après condition que le pointeur retourné ait la valeur null.  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   Le pointeur retourné pointe vers une mémoire tampon valide de taille `s` éléments ou d’octets.  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   Le pointeur retourné pointe vers une mémoire tampon de taille `s` éléments ou octets dont la première `c` est valide.  
  
  Certaines conventions d’interface présument que les paramètres de sortie sont annulés en cas d’échec.  À l’exception du code COM explicite, les formulaires répertoriés dans le tableau suivant sont préférés.  Pour le code COM, utilisez les formulaires COM correspondants répertoriés dans la section précédente.  
  
  **Annotations et descriptions**  
  
- `_Result_nullonfailure_`  
  
   Modifie d’autres annotations. Le résultat est défini sur null si la fonction échoue.  
  
- `_Result_zeroonfailure_`  
  
   Modifie d’autres annotations. Le résultat est défini sur zéro si la fonction échoue.  
  
- `_Outptr_result_nullonfailure_`  
  
   Le pointeur retourné pointe vers une mémoire tampon valide si la fonction réussit, ou null si la fonction échoue. Cette annotation est destinée à un paramètre non facultatif.  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   Le pointeur retourné pointe vers une mémoire tampon valide si la fonction réussit, ou null si la fonction échoue. Cette annotation est destinée à un paramètre facultatif.  
  
- `_Outref_result_nullonfailure_`  
  
   Le pointeur retourné pointe vers une mémoire tampon valide si la fonction réussit, ou null si la fonction échoue. Cette annotation est destinée à un paramètre de référence.  
  
## <a name="output-reference-parameters"></a>Paramètres de référence de sortie  
 Le paramètre de référence est couramment utilisé pour les paramètres de sortie.  Pour les paramètres de référence de sortie simples, par exemple `int&`,`_Out_` fournit la sémantique correcte.  Toutefois, lorsque la valeur de sortie est un pointeur (par exemple `int *&`), les annotations de pointeur équivalentes comme `_Outptr_ int **` ne fournissent pas la sémantique correcte.  Pour exprimer de façon concise la sémantique des paramètres de référence de sortie pour les types pointeur, utilisez les annotations composites suivantes :  
  
 **Annotations et descriptions**  
  
- `_Outref_`  
  
     Le résultat doit être valide dans après l’État et ne peut pas être null.  
  
- `_Outref_result_maybenull_`  
  
     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans un État postérieur.  
  
- `_Outref_result_buffer_(s)`  
  
     Le résultat doit être valide dans après l’État et ne peut pas être null. Pointe vers la mémoire tampon valide de la taille `s` éléments.  
  
- `_Outref_result_bytebuffer_(s)`  
  
     Le résultat doit être valide dans après l’État et ne peut pas être null. Pointe vers une mémoire tampon valide de taille `s` octets.  
  
- `_Outref_result_buffer_to_(s, c)`  
  
     Le résultat doit être valide dans après l’État et ne peut pas être null. Pointe vers la mémoire tampon d’éléments `s` dont les premiers `c` sont valides.  
  
- `_Outref_result_bytebuffer_to_(s, c)`  
  
     Le résultat doit être valide dans après l’État et ne peut pas être null. Pointe vers la mémoire tampon de `s` octets dont le premier `c` est valide.  
  
- `_Outref_result_buffer_all_(s)`  
  
     Le résultat doit être valide dans après l’État et ne peut pas être null. Pointe vers une mémoire tampon valide de taille `s` éléments valides.  
  
- `_Outref_result_bytebuffer_all_(s)`  
  
     Le résultat doit être valide dans après l’État et ne peut pas être null. Pointe vers une mémoire tampon valide de `s` octets d’éléments valides.  
  
- `_Outref_result_buffer_maybenull_(s)`  
  
     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans un État postérieur. Pointe vers la mémoire tampon valide de la taille `s` éléments.  
  
- `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans un État postérieur. Pointe vers une mémoire tampon valide de taille `s` octets.  
  
- `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans un État postérieur. Pointe vers la mémoire tampon d’éléments `s` dont les premiers `c` sont valides.  
  
- `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans l’état de publication. Pointe vers la mémoire tampon de `s` octets dont le premier `c` est valide.  
  
- `_Outref_result_buffer_all_maybenull_(s)`  
  
     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans l’état de publication. Pointe vers une mémoire tampon valide de taille `s` éléments valides.  
  
- `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Le résultat doit être valide dans après l’État, mais peut avoir la valeur null dans l’état de publication. Pointe vers une mémoire tampon valide de `s` octets d’éléments valides.  
  
## <a name="return-values"></a>Valeurs de retour  
 La valeur de retour d’une fonction ressemble à un paramètre de `_Out_` mais se trouve à un niveau de déréférencement différent, et vous n’avez pas à considérer le concept du pointeur sur le résultat.  Pour les annotations suivantes, la valeur de retour est l’objet annoté (un scalaire, un pointeur vers un struct ou un pointeur vers une mémoire tampon). Ces annotations ont la même sémantique que l’annotation `_Out_` correspondante.  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>Autres annotations courantes  
 **Annotations et descriptions**  
  
- `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Le paramètre, le champ ou le résultat se trouve dans la plage (inclusive) de `low` à `hi`.  Équivaut à `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` qui est appliqué à l’objet annoté avec les conditions préalables ou postérieures à l’État appropriées.  
  
    > [!IMPORTANT]
    > Bien que les noms contiennent « in » et « out », la sémantique de `_In_` et `_Out_` ne s’appliquent **pas** à ces annotations.  
  
- `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     La valeur annotée est exactement `expr`.  Équivaut à `_Satisfies_(_Curr_ == expr)` qui est appliqué à l’objet annoté avec les conditions préalables ou postérieures à l’État appropriées.  
  
- `_Struct_size_bytes_(size)`  
  
     S’applique à une déclaration de classe ou de struct.  Indique qu’un objet valide de ce type peut être plus grand que le type déclaré, avec le nombre d’octets spécifié par `size`.  Par exemple :  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     La taille de la mémoire tampon en octets d’un paramètre `pM` de type `MyStruct *` est ensuite considérée comme :  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Ressources associées  
 [Blog de l’équipe d’analyse du code](https://blogs.msdn.com/b/codeanalysis/)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’annotations SAL pour réduireC++ les erreurs C/code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Compréhension](../code-quality/understanding-sal.md) des  SAL  
 [Annoter le comportement](../code-quality/annotating-function-behavior.md) de la fonction   
 [Annoter des structs et des Classes](../code-quality/annotating-structs-and-classes.md)   
 [Annoter le comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécification du moment et de l’endroit où une annotation s’applique](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)
