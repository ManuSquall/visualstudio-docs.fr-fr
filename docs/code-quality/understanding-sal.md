---
title: "Présentation de SAL | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 196bfdbeeda00199861ea2f676553f024fcaf98f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-sal"></a>Présentation de SAL
Le langage d’annotation du code source Microsoft (SAL) fournit un ensemble d’annotations que vous pouvez utiliser pour décrire comment une fonction utilise ses paramètres, les hypothèses sur lesquelles elle émet à leur sujet et les garanties qu’elle quand elle s’achève. Les annotations sont définies dans le fichier d’en-tête `<sal.h>`. Analyse du code Visual Studio pour C++ utilise des annotations SAL pour modifier son analyse de fonctions. Pour plus d’informations sur SAL 2.0 pour le développement de pilote Windows, consultez [Annotations SAL 2.0 pour Windows pilotes](http://go.microsoft.com/fwlink/?LinkId=250979).  
  
 En mode natif, C et C++ fournissent uniquement limitée aux développeurs de manière cohérente express intention et l’invariance. À l’aide des annotations SAL, vous pouvez décrire vos fonctions plus en détail afin que les développeurs qui utilisent leur peuvent de mieux comprendre comment les utiliser.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>Nouveautés SAL et pourquoi l’utiliser ?  
 En termes simples, SAL est un moyen peu coûteux pour permettre au compilateur de vérifier votre code pour vous.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL rend le Code plus précieux  
 SAL peut vous aider à rendre la conception de votre code plus compréhensible, pour les utilisateurs et les outils d’analyse du code. Considérez cet exemple qui illustre la fonction C runtime `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 Savoir ce que fait cette fonction ? Lorsqu’une fonction est implémentée ou appelée, certaines propriétés doivent être assurées pour garantir l’exactitude du programme. Il suffit à une déclaration telle que celle dans l’exemple, vous ne connaissez pas ce qu’ils sont. Sans les annotations SAL, vous devrez s’appuient sur la documentation ou des commentaires de code. Voici quelles la documentation MSDN pour `memcpy` indique :  
  
> « Copies comptent les octets de src vers la destination. Si la source et la destination se chevauchent, le comportement de memcpy est indéfini. Memmove permet de gérer les régions qui se chevauche.   
> **Note de sécurité :** vous assurer que la mémoire tampon de destination est la même taille ou supérieure à la mémoire tampon source. Pour plus d’informations, voir éviter les dépassements de mémoire tampon. »  
  
 La documentation contient deux bits d’information qui suggère que votre code doit conserver certaines propriétés pour garantir l’exactitude du programme :  
  
-   `memcpy`copie le `count` d’octets à partir de la mémoire tampon source à la mémoire tampon de destination.  
  
-   La mémoire tampon de destination doit être au moins aussi grande que la mémoire tampon source.  
  
 Toutefois, le compilateur ne peut pas lire la documentation ou des commentaires informelles. Il ne sait pas qu’il existe une relation entre les deux mémoires tampons et `count`, et elle aussi ne peut pas efficacement deviner sur une relation. SAL peut fournir plus de clarté sur les propriétés et l’implémentation de la fonction, comme indiqué ici :  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Notez que ces annotations ressemblent aux informations contenues dans la documentation MSDN, mais ils sont plus concises et elles suivent un modèle sémantique. Lorsque vous lisez ce code, vous pouvez comprendre rapidement les propriétés de cette fonction et comment éviter les problèmes de sécurité de dépassement de mémoire tampon. Mieux encore, les modèles sémantiques qui fournit des SAL peuvent améliorer l’efficacité et l’efficacité des outils d’analyse de code automatique dans la détection anticipée des bogues potentiels. Imaginez que quelqu'un écrit cette implémentation boguée de `wmemcpy`:  
  
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
  
 Cette implémentation contient une erreur de désactiver par un common. Heureusement, l’auteur du code inclus l’annotation de taille de mémoire tampon SAL, un outil d’analyse du code pourrait intercepter le bogue en analysant cette fonction uniquement.  
  
### <a name="sal-basics"></a>Principes de base SAL  
 SAL définit quatre types de paramètres, qui sont classés par le modèle d’utilisation de base.  
  
|Category|Annotation du paramètre|Description|  
|--------------|--------------------------|-----------------|  
|**Entrée de la fonction appelée**|`_In_`|Données sont passées à la fonction appelée et sont traitées comme étant en lecture seule.|  
|**Entrée à fonction appelée et de sortie à l’appelant**|`_Inout_`|Données utilisables sont transmises à la fonction et qu’elle sont potentiellement modifiées.|  
|**Sortie vers l’appelant**|`_Out_`|L’appelant fournit uniquement un espace pour la fonction appelée écrire dans. La fonction appelée écrit des données dans cet espace.|  
|**Sortie de pointeur vers l’appelant**|`_Outptr_`|Comme **appelant que la sortie**. La valeur retournée par la fonction appelée est un pointeur.|  
  
 Ces quatre annotations de base peuvent être explicites plus de différentes manières. Par défaut, les paramètres de pointeur annotés sont supposés pour être requis, ils doivent être non NULL pour la fonction réussisse. La variation couramment utilisée des annotations base indique qu’un paramètre de pointeur est facultatif, s’il est NULL, la fonction peut encore réussir dans son travail.  
  
 Ce tableau montre comment effectuer la distinction entre les paramètres obligatoires et facultatifs :  
  
||Les paramètres sont requis|Les paramètres sont facultatifs|  
|-|-----------------------------|-----------------------------|  
|**Entrée de la fonction appelée**|`_In_`|`_In_opt_`|  
|**Entrée à fonction appelée et de sortie à l’appelant**|`_Inout_`|`_Inout_opt_`|  
|**Sortie vers l’appelant**|`_Out_`|`_Out_opt_`|  
|**Sortie de pointeur vers l’appelant**|`_Outptr_`|`_Outptr_opt_`|  
  
 Ces annotations aider à identifier les valeurs possibles sans être initialisé et utilise de pointeur null non valide de manière formelle et précise. Passage de NULL à un paramètre obligatoire peut provoquer un incident ou il peut entraîner un code d’erreur « Échec » doit être retournée. Dans les deux cas, la fonction ne peut pas réussir à cette fin de son travail.  
  
## <a name="sal-examples"></a>Exemples SAL  
 Cette section présente des exemples de code pour les annotations SAL base.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>À l’aide de l’outil d’analyse de Code Visual Studio à trouver des erreurs  
 Dans les exemples, l’outil d’analyse de Code Visual Studio est utilisé avec les annotations SAL pour rechercher les erreurs de code. Voici comment procéder.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Pour utiliser les outils d’analyse de code de Visual Studio et SAL  
  
1.  Dans Visual Studio, ouvrez un projet C++ qui contient les annotations SAL.  
  
2.  Dans la barre de menus, choisissez **générer**, **exécuter l’analyse du Code sur la Solution**.  
  
     Envisagez le _In\_ exemple dans cette section. Si vous exécutez l’analyse du code sur celui-ci, cet avertissement s’affiche :  
  
    > **C6387 Valeur de paramètre non valide**   
    > 'pointez' peut être '0' : Ceci n’est pas conforme à la spécification de la fonction 'InCallee'.  
  
### <a name="example-the-in-annotation"></a>Exemple : Le _In\_ Annotation  
 Le `_In_` annotation indique que :  
  
-   Le paramètre doit être valide et ne sera pas modifié.  
  
-   La fonction lit uniquement à partir du tampon de l’élément.  
  
-   L’appelant doit fournir la mémoire tampon et l’initialiser.  
  
-   `_In_`Spécifie « en lecture seule ». Une erreur courante consiste à appliquer `_In_` à un paramètre qui doit avoir le `_Inout_` annotation à la place.  
  
-   `_In_`est autorisé mais ignoré par l’Analyseur de pointeur non scalaires.  
  
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
  
 Si vous utilisez Visual Studio Code Analysis dans cet exemple, il vérifie que les appelants passer un pointeur non Null à un tampon initialisé pour `pInt`. Dans ce cas, `pInt` le pointeur ne peut pas être NULL.  
  
### <a name="example-the-inopt-annotation"></a>Exemple : Le _In_opt\_ Annotation  
 `_In_opt_`est le même que `_In_`, sauf que le paramètre d’entrée est autorisé à avoir la valeur NULL et, par conséquent, la fonction doit vérifier cela.  
  
```cpp  
  
void GoodInOptCallee(_In_opt_ int *pInt)  
{  
   if(pInt != NULL) {  
      int i = *pInt;  
   }  
}  
  
void BadInOptCallee(_In_opt_ int *pInt)  
{  
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
}  
  
void InOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOptCallee(pInt);  
   BadInOptCallee(pInt);  
}  
  
```  
  
 Analyse du Code Visual Studio valide que la fonction vérifie les valeurs NULL avant d’accéder à la mémoire tampon.  
  
### <a name="example-the-out-annotation"></a>Exemple : Le _Out\_ Annotation  
 `_Out_`prend en charge un scénario courant dans lequel un pointeur non NULL qui pointe vers une mémoire tampon d’élément est transmis et la fonction initialise l’élément. L’appelant ne possède pas d’initialisation de la mémoire tampon avant l’appel. la fonction appelée promet initialisez-le avant d’être retournée.  
  
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
  
 L’outil analyse de Code Visual Studio valide que l’appelant passe un pointeur non NULL dans une mémoire tampon pour `pInt` et que la mémoire tampon est initialisée par la fonction avant d’être retournée.  
  
### <a name="example-the-outopt-annotation"></a>Exemple : Le _Out_opt\_ Annotation  
 `_Out_opt_`est le même que `_Out_`, sauf que le paramètre peut être NULL et, par conséquent, la fonction doit vérifier cela.  
  
```cpp  
  
void GoodOutOptCallee(_Out_opt_ int *pInt)  
{  
   if (pInt != NULL) {  
      *pInt = 5;  
   }  
}  
  
void BadOutOptCallee(_Out_opt_ int *pInt)  
{  
   *pInt = 5; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutOptCaller()  
{  
   int *pInt = NULL;  
   GoodOutOptCallee(pInt);  
   BadOutOptCallee(pInt);  
}  
  
```  
  
 Analyse du Code Visual Studio valide que cette fonction vérifie les valeurs NULL avant `pInt` est déréférencé et si `pInt` n’est pas NULL, que la mémoire tampon est initialisée par la fonction avant d’être retournée.  
  
### <a name="example-the-inout-annotation"></a>Exemple : Le _Inout\_ Annotation  
 `_Inout_`est utilisé pour annoter un paramètre de pointeur qui peut être modifié par la fonction. Le pointeur doit pointer vers les données initialisées valides avant l’appel, et même si elle est modifiée, elle doit toujours avoir une valeur valide en retour. L’annotation indique que la fonction peut librement lire et écrire dans le tampon d’un élément. L’appelant doit fournir la mémoire tampon et l’initialiser.  
  
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
   InOutCallee(pInt); // 'pInt' should not be NULL  
}  
  
```  
  
 Analyse du Code Visual Studio vérifie que les appelants passer un pointeur non NULL à un tampon initialisé pour `pInt`et que, avant le retour, `pInt` est toujours non NULL et la mémoire tampon est initialisée.  
  
### <a name="example-the-inoutopt-annotation"></a>Exemple : Le _Inout_opt\_ Annotation  
 `_Inout_opt_`est le même que `_Inout_`, sauf que le paramètre d’entrée est autorisé à avoir la valeur NULL et, par conséquent, la fonction doit vérifier cela.  
  
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
   int i = *pInt; // Dereferencing NULL pointer 'pInt'  
   *pInt = 6;  
}  
  
void InOutOptCaller()  
{  
   int *pInt = NULL;  
   GoodInOutOptCallee(pInt);  
   BadInOutOptCallee(pInt);  
}  
  
```  
  
 Analyse du Code Visual Studio valide que cette fonction vérifie les valeurs NULL avant d’accéder à la mémoire tampon et si `pInt` n’est pas NULL, que la mémoire tampon est initialisée par la fonction avant d’être retournée.  
  
### <a name="example-the-outptr-annotation"></a>Exemple : Le _Outptr\_ Annotation  
 `_Outptr_`est utilisé pour annoter un paramètre qui est conçue pour retourner un pointeur.  Le paramètre lui-même ne doit pas être NULL et la fonction appelée retourne un pointeur non NULL dedans, et ce pointeur pointe vers les données initialisées.  
  
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
  
 Analyse du Code Visual Studio valide que l’appelant passe un pointeur non NULL `*pInt`, et que la mémoire tampon est initialisée par la fonction avant d’être retournée.  
  
### <a name="example-the-outptropt-annotation"></a>Exemple : Le _Outptr_opt\_ Annotation  
 `_Outptr_opt_`est le même que `_Outptr_`, sauf que le paramètre est facultatif, l’appelant peut passer un pointeur NULL pour le paramètre.  
  
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
   *pInt = pInt2; // Dereferencing NULL pointer 'pInt'  
}  
  
void OutPtrOptCaller()  
{  
   int **ppInt = NULL;  
   GoodOutPtrOptCallee(ppInt);  
   BadOutPtrOptCallee(ppInt);  
}  
  
```  
  
 Analyse du Code Visual Studio valide que cette fonction vérifie les valeurs NULL avant `*pInt` est déréférencé, et que la mémoire tampon est initialisée par la fonction avant d’être retournée.  
  
### <a name="example-the-success-annotation-in-combination-with-out"></a>Exemple : Le _Success\_ Annotation en combinaison avec _Out\_  
 Les annotations peuvent être appliquées à la plupart des objets.  En particulier, vous pouvez annoter une fonction entière.  L’une des caractéristiques d’une fonction la plus évidentes est qu’elle peut réussir ou échouer. Mais comme l’association entre une mémoire tampon et sa taille, C/C++ ne peut pas exprimer fonction réussite ou l’échec. À l’aide de la `_Success_` annotation, vous pouvez dire la réussite d’une fonction ressemble à.  Le paramètre pour le `_Success_` annotation est simplement une expression que lorsqu’il a la valeur true indique que la fonction a réussi. L’expression peut être tout ce que l’analyseur d’annotation peut gérer. Les effets des annotations après le retour de la fonction sont applicables uniquement lorsque la fonction réussit. Cet exemple montre comment `_Success_` interagit avec `_Out_` pour effectuer l’opération droite. Vous pouvez utiliser le mot clé `return` pour représenter la valeur de retour.  
  
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
  
 Le `_Out_` annotation provoque l’analyse du Code Visual Studio pour valider que l’appelant passe un pointeur non NULL dans une mémoire tampon pour `pInt`, et que la mémoire tampon est initialisée par la fonction avant d’être retournée.  
  
## <a name="sal-best-practice"></a>Il est recommandé SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Ajout d’Annotations au Code existant  
 SAL est une technologie puissante et qui peut vous aider à améliorer la sécurité et la fiabilité de votre code. Une fois que vous découvrez SAL, vous pouvez appliquer les nouvelles compétences pour votre travail quotidien. Dans le nouveau code, vous pouvez utiliser des spécifications SAL par conception dans l’ensemble ; dans le code plus ancien, vous pouvez ajouter des annotations de façon incrémentielle et augmenter ainsi les avantages chaque fois que vous mettez à jour.  
  
 En-têtes publics de Microsoft sont déjà annotés. Par conséquent, nous vous suggérons que dans vos projets vous tout d’abord annotez des fonctions de nœud feuille et les fonctions qui appellent des API Win32 pour tirer le meilleur parti.  
  
### <a name="when-do-i-annotate"></a>Lorsque annoter  
 Voici quelques conseils :  
  
-   Annoter tous les paramètres de pointeur.  
  
-   Annoter les annotations de la plage de valeurs afin que l’analyse du Code peut garantir la sécurité de mémoire tampon et de pointeur.  
  
-   Annoter les règles de verrouillage et les effets secondaires du verrouillage. Pour plus d’informations, consultez [annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md).  
  
-   Annoter les propriétés du pilote et autres propriétés spécifiques à un domaine.  
  
 Ou bien, vous pouvez annoter tous les paramètres qui permettent de clarifier votre intention dans l’ensemble et pour faciliter le travail vérifier que les annotations ont été effectuées.  
  
## <a name="related-resources"></a>Ressources connexes  
 [Blog de l’équipe analyse du code](http://go.microsoft.com/fwlink/p/?LinkId=251197)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’Annotations SAL pour réduire les défauts du Code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement de la fonction](../code-quality/annotating-function-behavior.md)   
 [Les structures et Classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécification de quand et où une Annotation est applicable](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Meilleures pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)