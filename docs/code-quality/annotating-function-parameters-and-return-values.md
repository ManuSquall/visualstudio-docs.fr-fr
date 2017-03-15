---
title: "Annotation de param&#232;tres de fonction et valeurs de retour | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Outptr_opt_result_bytebuffer_to_"
  - "_Inout_updates_all_opt_"
  - "_Post_equal_to_"
  - "_Outptr_opt_result_maybenull_"
  - "_Out_writes_bytes_all_"
  - "_Out_writes_all_opt_"
  - "_In_opt_"
  - "_Outptr_"
  - "_Outptr_result_maybenull_"
  - "_Outref_result_bytebuffer_all_maybenull_"
  - "_Inout_updates_opt_z_"
  - "_Inout_updates_z_"
  - "_Out_writes_"
  - "_Out_writes_to_ptr_opt_z_"
  - "_In_reads_to_ptr_opt_"
  - "_Ret_writes_to_maybenull_"
  - "_Outref_result_maybenull_"
  - "_Ret_writes_bytes_"
  - "_Outptr_result_bytebuffer_"
  - "_Out_writes_opt_"
  - "_Inout_updates_bytes_opt_"
  - "_In_z_"
  - "_Inout_updates_to_"
  - "_Ret_maybenull_"
  - "_Ret_writes_bytes_to_"
  - "_Ret_z_"
  - "_COM_Outptr_"
  - "_Ret_maybenull_z_"
  - "_Out_opt_"
  - "_In_reads_opt_z_"
  - "_Outptr_result_bytebuffer_to_"
  - "_Ret_notnull_"
  - "_COM_Outptr_opt_result_maybenull_"
  - "_Inout_updates_to_opt_"
  - "_Inout_updates_"
  - "_Outptr_opt_result_buffer_"
  - "_Outptr_result_buffer_to_"
  - "_Out_writes_to_ptr_opt_"
  - "_Out_writes_bytes_all_opt_"
  - "_Inout_updates_all_"
  - "_Deref_inout_range_"
  - "_Ret_writes_"
  - "_Out_writes_z_"
  - "_Ret_writes_to_"
  - "_Out_writes_to_ptr_z_"
  - "_Out_writes_bytes_to_opt_"
  - "_In_reads_or_z_"
  - "_Inout_updates_bytes_to_"
  - "_In_reads_z_"
  - "_In_opt_z_"
  - "_Outref_result_buffer_maybenull_"
  - "_Ret_range_"
  - "_COM_Outptr_opt_"
  - "_Ouptr_opt_result_maybenull_z_"
  - "_In_reads_opt_"
  - "_Inout_"
  - "_Field_range_"
  - "_Ret_writes_z_"
  - "_Out_writes_to_"
  - "_Out_writes_to_ptr_"
  - "_Inout_opt_z_"
  - "_Outref_"
  - "_Deref_out_range_"
  - "_Outref_result_buffer_"
  - "_Outref_result_buffer_to_"
  - "_Outref_result_bytebuffer_to_maybenull_"
  - "_In_reads_bytes_"
  - "_Outptr_opt_result_buffer_to_"
  - "_Outref_result_buffer_all_"
  - "_Out_writes_bytes_to_"
  - "_Result_zeroonfailure_"
  - "_In_reads_bytes_opt_"
  - "_Outref_result_buffer_to_maybenull_"
  - "_Outref_result_bytebuffer_all_"
  - "_Outref_result_buffer_all_maybenull_"
  - "_Ret_writes_maybenull_z_"
  - "_In_range_"
  - "_Inout_updates_bytes_all_opt_"
  - "_Outref_result_bytebuffer_to_"
  - "_Inout_updates_bytes_to_opt_"
  - "_Pre_equal_to_"
  - "_Ret_writes_bytes_maybenull_"
  - "_COM_Outptr_result_maybenull_"
  - "_Ret_writes_maybenull_"
  - "_Out_writes_bytes_"
  - "_Outptr_opt_"
  - "_Out_writes_opt_z_"
  - "_Outref_result_nullonfailure_"
  - "_Outptr_opt_result_z_"
  - "_Inout_opt_"
  - "_Deref_in_range_"
  - "_Outptr_result_z_"
  - "_In_reads_to_ptr_opt_z_"
  - "_Struct_size_bytes_"
  - "_Outptr_result_nullonfailure_"
  - "_In_"
  - "_Inout_updates_bytes_"
  - "_In_reads_to_ptr_z_"
  - "_Ret_writes_bytes_to_maybenull"
  - "_Outptr_opt_result_nullonfailure_"
  - "_In_reads_to_ptr_"
  - "_Outptr_result_buffer_"
  - "_Out_"
  - "_Outref_result_bytebuffer_maybenull_"
  - "_Outptr_result_maybenull_z_"
  - "_In_reads_"
  - "_Inout_updates_opt_"
  - "_Out_writes_to_opt_"
  - "_Outptr_opt_result_bytebuffer_"
  - "_Out_writes_all_"
  - "_Out_range_"
  - "_Inout_updates_bytes_all_"
  - "_Inout_z_"
  - "_Outref_result_bytebuffer_"
  - "_Result_nullonfailure_"
  - "_Ret_null_"
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Annotation de param&#232;tres de fonction et valeurs de retour
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cet article décrit les utilisations courantes des annotations pour les paramètres de fonction simple, scalaires et des pointeurs vers des classes et structures et la plupart des types de mémoires tampons.  Cet article explique également les modèles d’utilisation courants pour les annotations. Pour les annotations supplémentaires qui sont liées à des fonctions, consultez [annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>Paramètres de pointeur  
 Pour les annotations dans le tableau suivant, un paramètre de pointeur est annoté, l’analyseur signale une erreur si le pointeur est null.  Cela s’applique aux pointeurs et à des éléments de données qui sont indiqué.  
  
 **Annotations et Descriptions**  
  
-   `_In_`  
  
     Annote les paramètres d’entrée sont des valeurs scalaires, des structures, des pointeurs vers des structures et autres.  Explicitement peut être utilisé sur des valeurs scalaires simples.  Le paramètre doit être valide dans l’état préliminaire et ne sera pas modifié.  
  
-   `_Out_`  
  
     Annote les paramètres de sortie qui sont des valeurs scalaires, des structures, des pointeurs vers des structures et autres.  N’appliquez pas ce à un objet qui ne peut pas retourner une valeur, par exemple, une valeur scalaire qui est passée par valeur.  Le paramètre ne devra pas être valide dans l’état préalable mais doit être valide dans l’état postérieur à.  
  
-   `_Inout_`  
  
     Annote un paramètre qui est modifié par la fonction.  Il doit être valide à la fois état avant ou après, mais il est supposé pour avoir des valeurs différentes avant et après l’appel. Appliquez à une valeur modifiable.  
  
-   `_In_z_`  
  
     Pointeur vers une chaîne terminée par le caractère null qui est utilisé comme entrée.  La chaîne doit être valide dans l’état préalable.  Variantes de `PSTR`, lequel déjà les annotations correctes, sont par défaut.  
  
-   `_Inout_z_`  
  
     Pointeur vers un tableau de caractères se terminant par null qui sera modifié.  Il doit être valide avant et après l’appel, mais la valeur par défaut ont été modifiés.  La marque de fin null peut-être être déplacé, mais uniquement les éléments jusqu'à la marque de fin null d’origine est accessible.  
  
-   `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Pointeur vers un tableau, qui est lu par la fonction.  Le tableau est de taille `s` éléments, qui doit être valide.  
  
     Le `_bytes_` variante donne la taille en octets plutôt que des éléments. Utilisez-le uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, `char` chaînes utiliseraient la `_bytes_` variante uniquement si la même fonction qu’utilise `wchar_t` serait.  
  
-   `_In_reads_z_(s)`  
  
     Pointeur vers un tableau qui est terminée et a une taille connue. Les éléments jusqu'à la marque de fin null, ou `s` Si aucune marque de fin null, état doit être valide avant.  Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  
  
-   `_In_reads_or_z_(s)`  
  
     Pointeur vers un tableau qui est terminée ou a une taille connue, ou les deux. Les éléments jusqu'à la marque de fin null, ou `s` Si aucune marque de fin null, état doit être valide avant.  Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  (Utilisé pour le `strn` famille.)  
  
-   `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Un pointeur vers un tableau de `s` (gestion d’éléments octets) qui sera écrite par la fonction.  Les éléments du tableau est inutile être valide dans l’état préalable et le nombre d’éléments qui sont valides dans l’état postérieur à n’est pas spécifié.  S’il existe des annotations sur le type de paramètre, elles sont appliquées dans l’état postérieur à. Par exemple, prenons le code suivant.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     Dans cet exemple, l’appelant fournit une mémoire tampon de `size` éléments pour `p1`.  `MyStringCopy` certains de ces éléments est valide. Plus important encore, le `_Null_terminated_` annotation sur `PWSTR` signifie que `p1` est nul dans l’état postérieur à.  De cette façon, le nombre d’éléments valides est toujours bien défini, mais un nombre d’éléments spécifique n’est pas requis.  
  
     Le `_bytes_` variante donne la taille en octets plutôt que des éléments. Utilisez-le uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, `char` chaînes utiliseraient la `_bytes_` variante uniquement si la même fonction qu’utilise `wchar_t` serait.  
  
-   `_Out_writes_z_(s)`  
  
     Un pointeur vers un tableau de `s` éléments.  Les éléments n’ont pas soit valide dans l’état préalable.  État après, les éléments de configuration via le terminateur null, qui doit être présent, doit être valide.  Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  
  
-   `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Pointeur vers un tableau, qui est à la fois lues et écrit dans la fonction.  Il est de taille `s` éléments et valide état avant ou après.  
  
     Le `_bytes_` variante donne la taille en octets plutôt que des éléments. Utilisez-le uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, `char` chaînes utiliseraient la `_bytes_` variante uniquement si la même fonction qu’utilise `wchar_t` serait.  
  
-   `_Inout_updates_z_(s)`  
  
     Pointeur vers un tableau qui est terminée et a une taille connue. Les éléments de configuration via le terminateur null, qui doit être présent, doit être valide à la fois état avant ou après.  La valeur de l’état postérieur à est censée être différente de la valeur dans l’état préalable ; Cela inclut l’emplacement de la marque de fin null. Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Un pointeur vers un tableau de `s` éléments.  Les éléments n’ont pas soit valide dans l’état préalable.  État après, les éléments jusqu'à la `c`-ième élément doit être valide.  Si la taille est connue en octets, à l’échelle `s` et `c` par la taille de l’élément ou l’utilisation du `_bytes_` variante, qui est défini comme :  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     En d’autres termes, chaque élément qui existe dans la mémoire tampon jusqu'à `s` dans l’état préliminaire est valide dans l’état postérieur à.  Exemple :  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Pointeur vers un tableau, qui est lue et modifiée par la fonction.  Il est de taille `s` éléments, qui doit être valide dans l’état préalable, et `c` éléments doivent être valides dans l’état postérieur à.  
  
     Le `_bytes_` variante donne la taille en octets plutôt que des éléments. Utilisez-le uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, `char` chaînes utiliseraient la `_bytes_` variante uniquement si la même fonction qu’utilise `wchar_t` serait.  
  
-   `_Inout_updates_z_(s)`  
  
     Pointeur vers un tableau qui est terminée et a une taille connue. Les éléments de configuration via le terminateur null, qui doit être présent, doit être valide à la fois état avant ou après.  La valeur de l’état postérieur à est censée être différente de la valeur dans l’état préalable ; Cela inclut l’emplacement de la marque de fin null. Si la taille est connue en octets, à l’échelle `s` par la taille de l’élément.  
  
-   `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Un pointeur vers un tableau de `s` éléments.  Les éléments n’ont pas soit valide dans l’état préalable.  État après, les éléments jusqu'à la `c`-ième élément doit être valide.  Si la taille est connue en octets, à l’échelle `s` et `c` par la taille de l’élément ou l’utilisation du `_bytes_` variante, qui est défini comme :  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     En d’autres termes, chaque élément qui existe dans la mémoire tampon jusqu'à `s` dans l’état préliminaire est valide dans l’état postérieur à.  Exemple :  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
-   `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Pointeur vers un tableau, qui est lue et modifiée par la fonction.  Il est de taille `s` éléments, qui doit être valide dans l’état préalable, et `c` éléments doivent être valides dans l’état postérieur à.  
  
     Le `_bytes_` variante donne la taille en octets plutôt que des éléments. Utilisez-le uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, `char` chaînes utiliseraient la `_bytes_` variante uniquement si la même fonction qu’utilise `wchar_t` serait.  
  
-   `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Un pointeur vers un tableau, qui est lue et modifiée par la fonction de la taille `s` éléments. Défini comme équivalent à :  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     En d’autres termes, chaque élément qui existe dans la mémoire tampon jusqu'à `s` dans l’état préliminaire est valide l’état avant ou après.  
  
     Le `_bytes_` variante donne la taille en octets plutôt que des éléments. Utilisez-le uniquement lorsque la taille ne peut pas être exprimée en tant qu’éléments.  Par exemple, `char` chaînes utiliseraient la `_bytes_` variante uniquement si la même fonction qu’utilise `wchar_t` serait.  
  
-   `_In_reads_to_ptr_(p)`  
  
     Un pointeur vers un tableau pour lequel l’expression `p` – `_Curr_` (autrement dit, `p` moins `_Curr_`) est défini par la norme du langage approprié.  Les éléments antérieurs à `p` doit être valide dans l’état préalable.  
  
-   `_In_reads_to_ptr_z_(p)`  
  
     Un pointeur vers un tableau nul pour laquelle l’expression `p` – `_Curr_` (autrement dit, `p` moins `_Curr_`) est défini par la norme du langage approprié.  Les éléments antérieurs à `p` doit être valide dans l’état préalable.  
  
-   `_Out_writes_to_ptr_(p)`  
  
     Un pointeur vers un tableau pour lequel l’expression `p` – `_Curr_` (autrement dit, `p` moins `_Curr_`) est défini par la norme du langage approprié.  Les éléments antérieurs à `p` n’ont pas à être valides dans un état avant et doit être valide dans l’état postérieur à.  
  
-   `_Out_writes_to_ptr_z_(p)`  
  
     Un pointeur vers un tableau nul pour laquelle l’expression `p` – `_Curr_` (autrement dit, `p` moins `_Curr_`) est défini par la norme du langage approprié.  Les éléments antérieurs à `p` n’ont pas à être valides dans un état avant et doit être valide dans l’état postérieur à.  
  
## <a name="optional-pointer-parameters"></a>Paramètres de pointeur facultatif  
 Lorsqu’une annotation de paramètre de pointeur inclut `_opt_`, il indique que le paramètre peut être null. Dans le cas contraire, l’annotation effectue la même que la version qui n’inclut pas `_opt_`. Voici une liste de la `_opt_` variantes des annotations de paramètre de pointeur :  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Paramètres de pointeur de sortie  
 Paramètres de pointeur de sortie requièrent une notation spéciale pour lever l’ambiguïté de nullité sur le paramètre et l’emplacement désigné.  
  
 **Annotations et Descriptions**  
  
-   `_Outptr_`  
  
     Paramètre ne peut pas être null et, dans l’état postérieur à l’emplacement désigné ne peut pas être null et doit être valide.  
  
-   `_Outptr_opt_`  
  
     Paramètre peut être null, mais l’état postérieur à l’emplacement pointé ne peut pas être null et doit être valide.  
  
-   `_Outptr_result_maybenull_`  
  
     Paramètre ne peut pas être null, et dans l’état postérieur à l’emplacement désigné peut être null.  
  
-   `_Outptr_opt_result_maybenull_`  
  
     Paramètre peut être null, et dans l’état postérieur à l’emplacement désigné peut être null.  
  
 Dans le tableau suivant, les sous-chaînes supplémentaires sont insérées dans le nom de l’annotation afin de qualifier davantage la signification de l’annotation.  Les sous-chaînes différentes sont `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, et `_to_`.  
  
> [!IMPORTANT]
>  Si l’interface que vous annotez COM, utilisez la forme COM de ces annotations. N’utilisez pas les annotations COM avec toute autre interface de type.  
  
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
  
     Le pointeur retourné pointe vers un tampon de taille valid `s` éléments ou octets.  
  
-   `_Outptr_result_buffer_to_(s, c)`  
  
     `_Outptr_result_bytebuffer_to_(s, c)`  
  
     `_Outptr_opt_result_buffer_to_(s,c)`  
  
     `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
     Le pointeur retourné pointe vers une mémoire tampon de taille `s` éléments ou octets dont la première `c` sont valides.  
  
 Certaines conventions interface supposent que les paramètres de sortie sont compensés en cas d’échec.  À l’exception du code explicitement COM, les formulaires dans le tableau suivant sont préférables.  Pour le code COM, utilisez les formats COM correspondants qui sont répertoriés dans la section précédente.  
  
 **Annotations et Descriptions**  
  
-   `_Result_nullonfailure_`  
  
     Modifie les autres annotations. Le résultat a la valeur null si la fonction échoue.  
  
-   `_Result_zeroonfailure_`  
  
     Modifie les autres annotations. Le résultat est défini sur zéro si la fonction échoue.  
  
-   `_Outptr_result_nullonfailure_`  
  
     Le pointeur retourné pointe vers une mémoire tampon valide si la fonction réussit, ou null si la fonction échoue. Cette annotation est un paramètre non facultatif.  
  
-   `_Outptr_opt_result_nullonfailure_`  
  
     Le pointeur retourné pointe vers une mémoire tampon valide si la fonction réussit, ou null si la fonction échoue. Cette annotation est pour un paramètre optionnel.  
  
-   `_Outref_result_nullonfailure_`  
  
     Le pointeur retourné pointe vers une mémoire tampon valide si la fonction réussit, ou null si la fonction échoue. Cette annotation est pour un paramètre de référence.  
  
## <a name="output-reference-parameters"></a>Paramètres de référence de sortie  
 Une utilisation courante de paramètre de référence est pour les paramètres output.  Pour les paramètres de référence de sortie simple, par exemple, `int&``_Out_` fournit la sémantique appropriée.  Toutefois, lorsque la valeur de sortie est un pointeur, par exemple `int *&`telles que les annotations équivalentes pointeur `_Outptr_ int **` ne fournissent pas la sémantique appropriée.  Pour exprimer concise la sémantique de référence des paramètres de sortie pour les types pointeur, utilisez ces annotations composites :  
  
 **Annotations et Descriptions**  
  
-   `_Outref_`  
  
     Résultat doit être valide dans l’état postérieur à et ne peut pas être null.  
  
-   `_Outref_result_maybenull_`  
  
     Résultat doit être valide dans l’état postérieur à, mais peut être dans l’état postérieur à null.  
  
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
  
     Résultat doit être valide dans l’état postérieur à et ne peut pas être null. Pointe vers une mémoire tampon valide de `s` octets d’éléments valides.  
  
-   `_Outref_result_buffer_maybenull_(s)`  
  
     Résultat doit être valide dans l’état postérieur à, mais peut être dans l’état postérieur à null. Pointe vers une mémoire tampon valide de taille `s` éléments.  
  
-   `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Résultat doit être valide dans l’état postérieur à, mais peut être dans l’état postérieur à null. Pointe vers une mémoire tampon valide de taille `s` octets.  
  
-   `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Résultat doit être valide dans l’état postérieur à, mais peut être dans l’état postérieur à null. Pointe vers une mémoire tampon de `s` éléments, dont la première `c` sont valides.  
  
-   `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état de la publication. Pointe vers une mémoire tampon de `s` octets dont la première `c` sont valides.  
  
-   `_Outref_result_buffer_all_maybenull_(s)`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état de la publication. Pointe vers une mémoire tampon valide de taille `s` éléments valides.  
  
-   `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Résultat doit être valide dans l’état postérieur à, mais il peut être null dans l’état de la publication. Pointe vers une mémoire tampon valide de `s` octets d’éléments valides.  
  
## <a name="return-values"></a>Valeurs de retour  
 La valeur de retour d’une fonction ressemble à un `_Out_` paramètre mais elle est à un niveau différent de de-reference, et vous n’avez pas à prendre en compte le concept du pointeur vers le résultat.  Pour les annotations suivantes, la valeur de retour est l’objet annoté : un pointeur vers une mémoire tampon, un pointeur vers une structure ou une valeur scalaire. Ces annotations ont la même sémantique que `_Out_` annotation.  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>Autres Annotations courants  
 **Annotations et Descriptions**  
  
-   `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Le paramètre, le champ ou le résultat est dans la plage (limites incluses) à partir de `low` à `hi`.  Équivalent à `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` qui est appliqué à l’objet annoté avec les conditions d’états avant ou après l’état appropriées.  
  
    > [!IMPORTANT]
    >  Bien que les noms contiennent « in » et « sortie », la sémantique de `_In_` et `_Out_` faire **pas** s’appliquent à ces annotations.  
  
-   `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     La valeur annotée est exactement `expr`.  Équivalent à `_Satisfies_(_Curr_ == expr)` qui est appliqué à l’objet annoté avec les conditions d’états avant ou après l’état appropriées.  
  
-   `_Struct_size_bytes_(size)`  
  
     S’applique à une déclaration de classe ou de struct.  Indique qu’un objet valide de ce type peut être plus grand que le type déclaré, avec le nombre d’octets étant donnée par `size`.  Exemple :  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     La taille du tampon en octets d’un paramètre `pM` de type `MyStruct *` est ensuite utilisé :  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Ressources connexes  
 [Blog de l’équipe analyse du code](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Structures et Classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécifier quand et où une Annotation est applicable](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Meilleures pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)