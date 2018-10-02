---
title: Présentation de SAL | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae6b16cc7f69aaf365188c488416d35402de9ca4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493423"
---
# <a name="understanding-sal"></a>Présentation de SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [comprendre SAL](https://docs.microsoft.com/visualstudio/code-quality/understanding-sal).  
  
Le langage d’annotation du code source Microsoft (SAL) fournit un ensemble d’annotations que vous pouvez utiliser pour décrire la façon dont une fonction utilise ses paramètres, les hypothèses qu’elle fait sur eux et les garanties qu’elle apporte quand elle est terminée. Les annotations sont définies dans le fichier d’en-tête `<sal.h>`. Visual Studio analyse du code pour C++ utilise les annotations SAL pour modifier son analyse de fonctions. Pour plus d’informations sur SAL 2.0 pour le développement de pilotes Windows, consultez [Annotations SAL 2.0 pour Windows pilotes](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 En mode natif, C et C++ permettent uniquement limité pour les développeurs à exprimer de façon cohérente intention et l’invariance. À l’aide des annotations SAL, vous pouvez décrire vos fonctions de façon plus détaillée afin que les développeurs qui les consomment peuvent mieux comprendre comment les utiliser.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>What ' s SAL et pourquoi l’utiliser ?  
 En termes simples, SAL est une méthode peu onéreuse pour permettre au compilateur de vérifier votre code pour vous.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL permet de coder plus précieux  
 SAL peut vous aider à rendre la conception de votre code plus compréhensible, pour les humains et les outils d’analyse de code. Prenons l’exemple suivant qui illustre la fonction C runtime `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 Vous pouvez indiquer ce que fait cette fonction ? Lorsqu’une fonction est implémentée ou appelée, certaines propriétés doivent être maintenues pour assurer l’exactitude du programme. Simplement en examinant une déclaration telle que celle dans l’exemple, vous ne connaissez pas ce qu’ils sont. Sans annotations SAL, vous seriez obligé de s’appuient sur la documentation ou des commentaires de code. Voici la la documentation MSDN pour `memcpy` indique :  
  
> « Copies comptent les octets de src vers la destination. Si la source et la destination se chevauchent, le comportement de memcpy est indéfini. Memmove permet de gérer les régions qui se chevauchent.   
> **Note de sécurité :** vous assurer que la mémoire tampon de destination est la même taille ou supérieure à la mémoire tampon source. Pour plus d’informations, consultez dépassements de mémoire tampon. »  
  
 La documentation contient deux éléments d’information qui suggèrent que votre code doit conserver certaines propriétés pour assurer l’exactitude du programme :  
  
-   `memcpy` copie le `count` d’octets à partir de la mémoire tampon source à la mémoire tampon de destination.  
  
-   La mémoire tampon de destination doit être au moins aussi grande que la mémoire tampon source.  
  
 Toutefois, le compilateur ne peut pas lire la documentation ou les commentaires informelles. Il ne sait pas qu’il existe une relation entre deux mémoires tampons et `count`, et il également ne peut pas efficacement deviner à propos d’une relation. SAL peut fournir plus d’explications sur les propriétés et l’implémentation de la fonction, comme illustré ici :  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Notez que ces annotations ressemble aux informations dans la documentation MSDN, mais ils sont plus concis et ils suivent un modèle sémantique. Lorsque vous lisez ce code, vous pouvez rapidement comprendre les propriétés de cette fonction et comment éviter les problèmes de sécurité de dépassement de mémoire tampon. Mieux encore, les modèles sémantiques SAL fournit peuvent améliorer l’efficacité et l’efficacité des outils d’analyse de code automatisé de la détection anticipée des bogues potentiels. Imaginez que quelqu'un écrit cette implémentation boguée de `wmemcpy`:  
  
```cpp  
  
wchar_t * wmemcpy(  
   _Out_writes_all_(count) wchar_t *dest,   
   _In_reads_(count) const wchar_t *src,   
   size_t count)  
{  
   size_t i;  
   for (i = 0; i <= count; i++) { // BUG: off-by-one error  
      dest[i] = src[i];  
   }  
   return dest;  
}  
  
```  
  
 Cette implémentation contient une erreur d’off-en-un courants. Heureusement, l’auteur du code inclus l’annotation SAL la taille mémoire tampon, un outil d’analyse de code pourrait intercepter le bogue en analysant cette fonction uniquement.  
  
### <a name="sal-basics"></a>Principes fondamentaux SAL  
 SAL définit quatre types de base de paramètres qui sont classés par le modèle d’utilisation.  
  
|Category|Annotation de paramètre|Description|  
|--------------|--------------------------|-----------------|  
|**Entrée appelée (fonction)**|`_In_`|Données sont passées à la fonction appelée et sont considérées comme étant en lecture seule.|  
|**Entrée à appelé fonction et de sortie à l’appelant**|`_Inout_`|Données utilisables sont transmies à la fonction et potentiellement sont modifiées.|  
|**Sortie vers l’appelant**|`_Out_`|L’appelant fournit uniquement l’espace pour la fonction appelée écrire dans. La fonction appelée écrit des données dans cet espace.|  
|**Sortie de pointeur vers l’appelant**|`_Outptr_`|Comme **de sortie à appelant**. La valeur retournée par la fonction appelée est un pointeur.|  
  
 Ces quatre annotations de base peuvent être effectuées plus explicites de différentes manières. Par défaut, les paramètres de pointeur annotés sont supposés pour être requis, ils doivent être non NULL pour la fonction réussisse. La plus couramment utilisée variation des annotations base indique qu’un paramètre de pointeur est facultatif, si sa valeur est NULL, la fonction peut encore réussir dans faire son travail.  
  
 Ce tableau montre comment faire la distinction entre les paramètres obligatoires et facultatifs :  
  
||Paramètres sont obligatoires|Les paramètres sont facultatifs|  
|-|-----------------------------|-----------------------------|  
|**Entrée appelée (fonction)**|`_In_`|`_In_opt_`|  
|**Entrée à appelé fonction et de sortie à l’appelant**|`_Inout_`|`_Inout_opt_`|  
|**Sortie vers l’appelant**|`_Out_`|`_Out_opt_`|  
|**Sortie de pointeur vers l’appelant**|`_Outptr_`|`_Outptr_opt_`|  
  
 Ces annotations vous aider à identifier les valeurs possibles non initialisées et un pointeur null non valide utilise de manière formelle et précise. Passage de NULL à un paramètre obligatoire peut provoquer un incident, ou il peut entraîner un code d’erreur « Échec » doit être retourné. Dans les deux cas, la fonction ne peut pas réussir à bien son travail.  
  
## <a name="sal-examples"></a>Exemples SAL  
 Cette section présente des exemples de code pour les annotations SAL de base.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>À l’aide de l’outil d’analyse de Code Visual Studio pour détecter des erreurs  
 Dans les exemples, l’outil d’analyse de Code Visual Studio est utilisé avec les annotations SAL pour rechercher les erreurs de code. Voici comment procéder.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Pour utiliser les outils d’analyse de code de Visual Studio et SAL  
  
1.  Dans Visual Studio, ouvrez un projet C++ qui contient les annotations SAL.  
  
2.  Dans la barre de menus, choisissez **Build**, **exécuter l’analyse du Code sur la Solution**.  
  
     Envisagez le _In\_ exemple dans cette section. Si vous exécutez l’analyse du code sur celui-ci, cet avertissement s’affiche :  
  
    > **C6387 Valeur de paramètre non valide**   
    > « Que » peut être '0' : Ceci n’est pas conforme à la spécification de la fonction 'InCallee'.  
  
### <a name="example-the-in-annotation"></a>Exemple : Le _In\_ Annotation  
 Le `_In_` annotation indique que :  
  
-   Le paramètre doit être valide et ne sera pas modifié.  
  
-   La fonction lit uniquement à partir de la mémoire tampon seul élément.  
  
-   L’appelant doit fournir la mémoire tampon et l’initialiser.  
  
-   `_In_` Spécifie « read-only ». Une erreur courante consiste à appliquer `_In_` à un paramètre qui doit avoir le `_Inout_` annotation à la place.  
  
-   `_In_` est autorisé mais ignoré par l’Analyseur de valeurs scalaires non pointeur.  
  
```cpp  
void InCallee(_In_ int *pInt)  
{  
   int i = *pInt;  
}  
  
void GoodInCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
  
   InCallee(pInt);  
   delete pInt;     
}  
  
void BadInCaller()  
{  
   int *pInt = NULL;  
   InCallee(pInt); // pInt should not be NULL  
}  
  
```  
  
 Si vous utilisez Visual Studio Code Analysis sur cet exemple, il valide le fait que les appelants passer un pointeur non Null à une mémoire tampon initialisé pour `pInt`. Dans ce cas, `pInt` pointeur ne peut pas être NULL.  
  
### <a name="example-the-inopt-annotation"></a>Exemple : Le _In_opt\_ Annotation  
 `_In_opt_` est identique à `_In_`, sauf que le paramètre d’entrée est autorisé à avoir la valeur NULL et, par conséquent, la fonction doit vérifier cela.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Analyse du Code Visual Studio valide le fait que la fonction vérifie les valeurs NULL avant d’accéder à la mémoire tampon.  
  
### <a name="example-the-out-annotation"></a>Exemple : Le _Out\_ Annotation  
 `_Out_` prend en charge un scénario courant dans lequel un pointeur non NULL qui pointe vers une mémoire tampon d’élément est transmis et la fonction initialise l’élément. L’appelant ne possède pas d’initialiser la mémoire tampon avant l’appel ; la fonction appelée promet d’initialiser avant de retourner.  
  
```cpp  
  
void GoodOutCallee(_Out_ int *pInt)  
{  
   *pInt = 5;  
}  
  
void BadOutCallee(_Out_ int *pInt)  
{  
   // Did not initialize pInt buffer before returning!  
}  
  
void OutCaller()  
{  
   int *pInt = new int;  
   GoodOutCallee(pInt);  
   BadOutCallee(pInt);  
   delete pInt;  
}  
  
```  
  
 L’outil analyse de Code Visual Studio valide le fait que l’appelant passe un pointeur non NULL dans une mémoire tampon pour `pInt` et que la mémoire tampon est initialisée par la fonction avant de retourner.  
  
### <a name="example-the-outopt-annotation"></a>Exemple : Le _Out_opt\_ Annotation  
 `_Out_opt_` est identique à `_Out_`, sauf que le paramètre ne peut pas être NULL et, par conséquent, la fonction doit vérifier cela.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Analyse du Code Visual Studio valide le fait que cette fonction vérifie les valeurs NULL avant `pInt` est déréférencé et si `pInt` n’est pas NULL, que la mémoire tampon est initialisée par la fonction avant de retourner.  
  
### <a name="example-the-inout-annotation"></a>Exemple : Le _Inout\_ Annotation  
 `_Inout_` est utilisé pour annoter un paramètre de pointeur qui peut être modifié par la fonction. Le pointeur doit pointer vers les données initialisées valides avant l’appel, et même si elle est modifiée, elle doit toujours avoir une valeur valide en retour. L’annotation Spécifie que la fonction peut librement lire et écrire dans la mémoire tampon d’un élément. L’appelant doit fournir la mémoire tampon et l’initialiser.  
  
> [!NOTE]
>  Comme `_Out_`, `_Inout_` doivent s’appliquer à une valeur modifiable.  
  
```cpp  
  
void InOutCallee(_Inout_ int *pInt)  
{  
   int i = *pInt;  
   *pInt = 6;  
}  
  
void InOutCaller()  
{  
   int *pInt = new int;  
   *pInt = 5;  
   InOutCallee(pInt);  
   delete pInt;  
}  
  
void BadInOutCaller()  
{  
   int *pInt = NULL;  
   InOutCallee(pInt); // ‘pInt’ should not be NULL  
}  
  
```  
  
 Analyse du Code Visual Studio valide le fait que les appelants passer un pointeur non NULL à une mémoire tampon initialisé pour `pInt`et que, avant le retour, `pInt` est toujours non NULL et la mémoire tampon est initialisée.  
  
### <a name="example-the-inoutopt-annotation"></a>Exemple : Le _Inout_opt\_ Annotation  
 `_Inout_opt_` est identique à `_Inout_`, sauf que le paramètre d’entrée est autorisé à avoir la valeur NULL et, par conséquent, la fonction doit vérifier cela.  
  
```cpp  
  
void GoodInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
      *pInt = 6;  
   }  
}  
  
void BadInOutOptCallee(_Inout_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer ‘pInt’  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Analyse du Code Visual Studio valide le fait que cette fonction vérifie les valeurs NULL avant d’accéder à la mémoire tampon et si `pInt` n’est pas NULL, que la mémoire tampon est initialisée par la fonction avant de retourner.  
  
### <a name="example-the-outptr-annotation"></a>Exemple : Le _Outptr\_ Annotation  
 `_Outptr_` est utilisé pour annoter un paramètre destiné à retourner un pointeur.  Le paramètre lui-même ne doit pas être NULL et la fonction appelée retourne un pointeur non NULL qu’il contient et ce pointeur pointe vers les données initialisées.  
  
```cpp  
  
void GoodOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 5;  
  
   *pInt = pInt2;  
}  
  
void BadOutPtrCallee(_Outptr_ int **pInt)  
{  
   int *pInt2 = new int;  
   // Did not initialize pInt buffer before returning!  
   *pInt = pInt2;  
}  
  
void OutPtrCaller()  
{  
   int *pInt = NULL;  
   GoodOutPtrCallee(&pInt);  
   BadOutPtrCallee(&pInt);  
}  
  
```  
  
 Analyse du Code Visual Studio valide le fait que l’appelant passe un pointeur non NULL `*pInt`, et que la mémoire tampon est initialisée par la fonction avant de retourner.  
  
### <a name="example-the-outptropt-annotation"></a>Exemple : Le _Outptr_opt\_ Annotation  
 `_Outptr_opt_` est identique à `_Outptr_`, sauf que le paramètre est facultatif, l’appelant peut passer un pointeur NULL pour le paramètre.  
  
```cpp  
  
void GoodOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
  
   if(pInt != NULL) {  
      *pInt = pInt2;  
   }  
}  
  
void BadOutPtrOptCallee(_Outptr_opt_ int **pInt)  
{  
   int *pInt2 = new int;  
   *pInt2 = 6;  
   *pInt = pInt2; // Dereferencing NULL pointer ‘pInt’  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Analyse du Code Visual Studio valide le fait que cette fonction vérifie les valeurs NULL avant `*pInt` est déréférencé, et que la mémoire tampon est initialisée par la fonction avant de retourner.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>Exemple : Le _Success\_ Annotation en combinaison avec _Out\_  
 Annotations peuvent être appliquées à la plupart des objets.  En particulier, vous pouvez annoter une fonction entière.  L’une des caractéristiques d’une fonction plus évidents est qu’elle peut réussir ou échouer. Mais comme l’association entre une mémoire tampon et sa taille, C/C++ ne peut pas exprimer fonction réussite ou l’échec. À l’aide de la `_Success_` annotation, que vous pouvez déterminer la réussite d’une fonction ressemble.  Le paramètre à la `_Success_` annotation est simplement une expression que lorsqu’il est true indique que la fonction a réussi. L’expression peut être tout ce que l’analyseur d’annotation peut gérer. Les effets des annotations après le retour de la fonction sont appliquent uniquement lorsque la fonction réussit. Cet exemple montre comment `_Success_` interagit avec `_Out_` adoptent l’attitude. Vous pouvez utiliser le mot clé `return` pour représenter la valeur de retour.  
  
```cpp  
  
_Success_(return != false) // Can also be stated as _Success_(return)  
bool GetValue(_Out_ int *pInt, bool flag)  
{  
   if(flag) {  
      *pInt = 5;  
      return true;  
   } else {  
      return false;  
   }  
}  
  
```  
  
 Le `_Out_` annotation provoque Visual Studio Code Analysis pour valider que l’appelant passe un pointeur non NULL dans une mémoire tampon pour `pInt`, et que la mémoire tampon est initialisée par la fonction avant de retourner.  
  
## <a name="sal-best-practice"></a>Meilleure pratique SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Ajout d’Annotations au Code existant  
 SAL est une technologie puissante qui vous permet d’améliorer la sécurité et la fiabilité de votre code. Une fois que vous allez SAL, vous pouvez appliquer la nouvelle compétence à votre travail quotidien. Dans le nouveau code, vous pouvez utiliser des spécifications SAL par conception dans l’ensemble ; dans le code plus ancien, vous pouvez ajouter des annotations de façon incrémentielle et augmenter ainsi les avantages chaque fois que vous mettez à jour.  
  
 En-têtes publics de Microsoft sont annotées déjà. Par conséquent, nous vous suggérons que dans vos projets vous tout d’abord annotez des fonctions de nœud feuille et les fonctions qui appellent les API Win32 pour tirer le meilleur parti.  
  
### <a name="when-do-i-annotate"></a>Lorsque annoter  
 Voici quelques indications :  
  
-   Annoter tous les paramètres de pointeur.  
  
-   Annoter des annotations de la plage de valeurs afin que l’analyse du Code peut garantir la sécurité des mémoires tampons et pointeur.  
  
-   Annoter des règles de verrouillage et des effets secondaires du verrouillage. Pour plus d’informations, consultez [comportement de verrouillage annotant](../code-quality/annotating-locking-behavior.md).  
  
-   Annoter les propriétés du pilote et autres propriétés spécifiques à un domaine.  
  
 Ou vous pouvez annoter tous les paramètres pour clarifier votre intention tout au long de rendre et pour faciliter le travail vérifier que les annotations ont été effectuées.  
  
## <a name="related-resources"></a>Ressources connexes  
 [Blog de l’équipe analyse du code](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Annotation des paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Annoter les Classes et Structs](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécifiant le moment où une Annotation est applicable et](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)



