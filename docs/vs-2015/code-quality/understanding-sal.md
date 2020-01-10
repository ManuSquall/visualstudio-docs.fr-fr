---
title: Comprendre SAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: a94d6907-55f2-4874-9571-51d52d6edcfd
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: a184ad6ebc1b3fc2dc21b7a1774b37fef8d359ec
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848466"
---
# <a name="understanding-sal"></a>Présentation de SAL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le langage SAL (source-code d’annotation) de Microsoft fournit un ensemble d’annotations que vous pouvez utiliser pour décrire comment une fonction utilise ses paramètres, les hypothèses qu’elle émet à leur sujet et les garanties qu’elle effectue lorsqu’elle se termine. Les annotations sont définies dans le fichier d’en-tête `<sal.h>`. L’analyse du code Visual C++ Studio pour utilise des annotations SAL pour modifier son analyse des fonctions. Pour plus d’informations sur le développement de pilotes Windows SAL 2,0 pour Windows, consultez [les annotations sal 2,0 pour les pilotes Windows](https://msdn.microsoft.com/library/windows/hardware/hh454237.aspx).  
  
 En mode natif, C C++ et offrent uniquement des moyens limités aux développeurs d’exprimer de manière cohérente l’intention et l’invariance. À l’aide des annotations SAL, vous pouvez décrire vos fonctions plus en détail afin que les développeurs qui les utilisent puissent mieux comprendre comment les utiliser.  
  
## <a name="what-is-sal-and-why-should-you-use-it"></a>Qu’est-ce que SAL et pourquoi l’utiliser ?  
 Simplement exprimé, SAL est un moyen peu coûteux de permettre au compilateur de vérifier votre code pour vous.  
  
### <a name="sal-makes-code-more-valuable"></a>SAL rend le code plus précieux  
 SAL peut vous aider à rendre votre conception de code plus compréhensible, aussi bien pour l’homme que pour les outils d’analyse du code. Prenons l’exemple suivant qui illustre la fonction Runtime C `memcpy`:  
  
```cpp  
  
void * memcpy(  
   void *dest,   
   const void *src,   
   size_t count  
);  
  
```  
  
 Pouvez-vous indiquer ce que fait cette fonction ? Lorsqu’une fonction est implémentée ou appelée, certaines propriétés doivent être gérées pour garantir l’exactitude du programme. En examinant simplement une déclaration telle que celle de l’exemple, vous ne savez pas ce qu’elles sont. Sans annotations SAL, vous devez vous appuyer sur la documentation ou des commentaires de code. Voici ce que la documentation MSDN pour `memcpy` indique :  
  
> «Copie le nombre d’octets de SRC vers dest. Si la source et la destination se chevauchent, le comportement de memcpy n’est pas défini. Utilisez memmove pour gérer les régions qui se chevauchent.   
> **Remarque relative à la sécurité :** Assurez-vous que la taille de la mémoire tampon de destination est supérieure ou égale à la mémoire tampon source. Pour plus d’informations, consultez éviter les dépassements de mémoire tampon.»  
  
 La documentation contient quelques bits d’informations qui suggèrent que votre code doit gérer certaines propriétés pour garantir l’exactitude du programme :  
  
- `memcpy` copie le `count` d’octets de la mémoire tampon source vers la mémoire tampon de destination.  
  
- La mémoire tampon de destination doit être au moins aussi grande que la mémoire tampon source.  
  
  Toutefois, le compilateur ne peut pas lire la documentation ou des commentaires informels. Il ne sait pas qu’il existe une relation entre les deux mémoires tampons et `count`, et il ne peut pas non plus deviner une relation de manière efficace. SAL peut fournir plus de clarté sur les propriétés et l’implémentation de la fonction, comme illustré ici :  
  
```cpp  
  
void * memcpy(  
   _Out_writes_bytes_all_(count) void *dest,   
   _In_reads_bytes_(count) const void *src,   
   size_t count  
);  
```  
  
 Notez que ces annotations ressemblent aux informations contenues dans la documentation MSDN, mais qu’elles sont plus concises et qu’elles suivent un modèle sémantique. Lorsque vous lisez ce code, vous pouvez rapidement comprendre les propriétés de cette fonction et éviter les problèmes de sécurité de dépassement de mémoire tampon. Mieux encore, les modèles sémantiques fournis par SAL peuvent améliorer l’efficacité et l’efficacité des outils d’analyse du code automatisés lors de la découverte précoce des bogues potentiels. Imaginez que quelqu’un écrit cette implémentation de bogue de `wmemcpy`:  
  
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
  
 Cette implémentation contient une erreur courante. Heureusement, l’auteur du code comprenait l’annotation de la taille de la mémoire tampon SAL. un outil d’analyse du code pourrait intercepter le bogue en analysant uniquement cette fonction.  
  
### <a name="sal-basics"></a>Principes de base du SAL  
 SAL définit quatre types de paramètres de base, classés par modèle d’utilisation.  
  
|Catégorie|Annotation de paramètre|Description|  
|--------------|--------------------------|-----------------|  
|**Entrée de la fonction appelée**|`_In_`|Les données sont passées à la fonction appelée et sont traitées en lecture seule.|  
|**Entrée de la fonction appelée et sortie vers l’appelant**|`_Inout_`|Les données utilisables sont transmises à la fonction et peuvent éventuellement être modifiées.|  
|**Sortie vers l’appelant**|`_Out_`|L’appelant fournit uniquement de l’espace pour l’écriture de la fonction appelée. La fonction appelée écrit des données dans cet espace.|  
|**Sortie du pointeur vers l’appelant**|`_Outptr_`|Comme la **sortie vers l’appelant**. La valeur retournée par la fonction appelée est un pointeur.|  
  
 Ces quatre annotations de base peuvent être rendues plus explicites de différentes façons. Par défaut, les paramètres de pointeur annotés sont supposés être requis ; ils doivent être non NULL pour que la fonction aboutisse. La variation la plus couramment utilisée des annotations de base indique qu’un paramètre de pointeur est facultatif. Si la valeur est NULL, la fonction peut toujours effectuer son travail.  
  
 Ce tableau montre comment faire la distinction entre les paramètres obligatoires et facultatifs :  
  
||Des paramètres sont requis|Les paramètres sont facultatifs|  
|-|-----------------------------|-----------------------------|  
|**Entrée de la fonction appelée**|`_In_`|`_In_opt_`|  
|**Entrée de la fonction appelée et sortie vers l’appelant**|`_Inout_`|`_Inout_opt_`|  
|**Sortie vers l’appelant**|`_Out_`|`_Out_opt_`|  
|**Sortie du pointeur vers l’appelant**|`_Outptr_`|`_Outptr_opt_`|  
  
 Ces annotations permettent d’identifier les valeurs non initialisées possibles et les utilisations de pointeur null non valides de manière formelle et précise. Le passage de la valeur NULL à un paramètre requis peut provoquer un incident ou provoquer le renvoi d’un code d’erreur « Failed ». Dans les deux cas, la fonction ne peut pas mener à bien son travail.  
  
## <a name="sal-examples"></a>Exemples SAL  
 Cette section présente des exemples de code pour les annotations SAL de base.  
  
### <a name="using-the-visual-studio-code-analysis-tool-to-find-defects"></a>Utilisation de l’outil d’analyse de Visual Studio Code pour détecter les défauts  
 Dans les exemples, l’outil d’analyse de Visual Studio Code est utilisé avec les annotations SAL pour rechercher les erreurs de code. Voici comment procéder.  
  
##### <a name="to-use-visual-studio-code-analysis-tools-and-sal"></a>Pour utiliser les outils d’analyse du code Visual Studio et SAL  
  
1. Dans Visual Studio, ouvrez un C++ projet qui contient des annotations SAL.  
  
2. Dans la barre de menus, choisissez **générer**, **exécuter l’analyse du code sur la solution**.  
  
    Prenez en compte les \_dans\_ exemple de cette section. Si vous exécutez l’analyse du code sur celle-ci, cet avertissement s’affiche :  
  
   > **C6387 valeur de paramètre non valide**   
   > 'pInte’peut être' 0 ' : Ceci n’est pas conforme à la spécification de la fonction’incalle'.  
  
### <a name="example-the-_in_-annotation"></a>Exemple : \_dans\_ annotation  
 L’annotation de `_In_` indique que :  
  
- Le paramètre doit être valide et ne sera pas modifié.  
  
- La fonction lira uniquement à partir de la mémoire tampon d’un seul élément.  
  
- L’appelant doit fournir la mémoire tampon et l’initialiser.  
  
- `_In_` spécifie « lecture seule ». Une erreur courante consiste à appliquer `_In_` à un paramètre qui doit avoir l’annotation `_Inout_` à la place.  
  
- `_In_` est autorisé mais ignoré par l’analyseur sur les valeurs scalaires non-pointeur.  
  
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
  
 Si vous utilisez Visual Studio Code analyse sur cet exemple, il vérifie que les appelants passent un pointeur non null à une mémoire tampon initialisée pour `pInt`. Dans ce cas, `pInt` pointeur ne peut pas avoir la valeur NULL.  
  
### <a name="example-the-_in_opt_-annotation"></a>Exemple : \_In_opt\_ annotation  
 `_In_opt_` est identique à `_In_`, sauf que le paramètre d’entrée peut être NULL et, par conséquent, la fonction doit vérifier cela.  
  
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
  
 Visual Studio Code analyse vérifie que la fonction recherche la valeur NULL avant d’accéder à la mémoire tampon.  
  
### <a name="example-the-_out_-annotation"></a>Exemple : \_out\_ annotation  
 `_Out_` prend en charge un scénario courant dans lequel un pointeur non NULL qui pointe vers une mémoire tampon d’élément est passé et la fonction initialise l’élément. L’appelant n’a pas besoin d’initialiser la mémoire tampon avant l’appel ; la fonction appelée promet de l’initialiser avant de retourner la valeur.  
  
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
  
 Visual Studio Code outil d’analyse vérifie que l’appelant passe un pointeur non NULL à une mémoire tampon pour `pInt` et que la mémoire tampon est initialisée par la fonction avant qu’elle ne soit retournée.  
  
### <a name="example-the-_out_opt_-annotation"></a>Exemple : \_Out_opt\_ annotation  
 `_Out_opt_` est identique à `_Out_`, sauf que le paramètre peut avoir la valeur NULL et, par conséquent, la fonction doit vérifier cela.  
  
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
  
 Visual Studio Code analyse vérifie que cette fonction recherche la valeur NULL avant que `pInt` soit déréférencée, et si `pInt` n’a pas la valeur NULL, que la mémoire tampon est initialisée par la fonction avant son retour.  
  
### <a name="example-the-_inout_-annotation"></a>Exemple : \_INOUT\_ annotation  
 `_Inout_` est utilisé pour annoter un paramètre de pointeur qui peut être modifié par la fonction. Le pointeur doit pointer vers des données initialisées valides avant l’appel, et même s’il est modifié, il doit toujours avoir une valeur valide au retour. L’annotation spécifie que la fonction peut lire et écrire librement dans la mémoire tampon d’un élément. L’appelant doit fournir la mémoire tampon et l’initialiser.  
  
> [!NOTE]
> Comme `_Out_`, `_Inout_` doit s’appliquer à une valeur modifiable.  
  
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
  
 Visual Studio Code analyse vérifie que les appelants passent un pointeur non NULL à une mémoire tampon initialisée pour `pInt`et que, avant le retour, `pInt` est toujours non NULL et que la mémoire tampon est initialisée.  
  
### <a name="example-the-_inout_opt_-annotation"></a>Exemple : \_Inout_opt\_ annotation  
 `_Inout_opt_` est identique à `_Inout_`, sauf que le paramètre d’entrée peut être NULL et, par conséquent, la fonction doit vérifier cela.  
  
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
  
 Visual Studio Code analyse vérifie que cette fonction recherche la valeur NULL avant d’accéder à la mémoire tampon, et si `pInt` n’a pas la valeur NULL, la mémoire tampon est initialisée par la fonction avant d’être retournée.  
  
### <a name="example-the-_outptr_-annotation"></a>Exemple : l’annotation \_Outptr\_  
 `_Outptr_` est utilisé pour annoter un paramètre destiné à retourner un pointeur.  Le paramètre lui-même ne doit pas avoir la valeur NULL, et la fonction appelée retourne un pointeur non NULL dans celui-ci et ce pointeur pointe vers les données initialisées.  
  
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
  
 Visual Studio Code analyse vérifie que l’appelant passe un pointeur non NULL pour `*pInt`, et que la mémoire tampon est initialisée par la fonction avant qu’elle ne soit retournée.  
  
### <a name="example-the-_outptr_opt_-annotation"></a>Exemple : \_Outptr_opt\_ annotation  
 `_Outptr_opt_` est identique à `_Outptr_`, sauf que le paramètre est facultatif : l’appelant peut passer un pointeur NULL pour le paramètre.  
  
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
  
 Visual Studio Code analyse vérifie que cette fonction recherche la valeur NULL avant que `*pInt` soit déréférencée, et que la mémoire tampon soit initialisée par la fonction avant qu’elle ne soit retournée.  
  
### <a name="example-the-_success_-annotation-in-combination-with-_out_"></a>Exemple : l’annotation de réussite de la \_\_ en combinaison avec \_\_  
 Les annotations peuvent être appliquées à la plupart des objets.  En particulier, vous pouvez annoter une fonction entière.  L’une des caractéristiques les plus évidentes d’une fonction est qu’elle peut réussir ou échouer. Mais comme l’association entre une mémoire tampon et sa taille, CC++ /ne peut pas exprimer la réussite ou l’échec de la fonction. À l’aide de l’annotation `_Success_`, vous pouvez indiquer la réussite d’une fonction.  Le paramètre de l’annotation `_Success_` est simplement une expression qui, lorsqu’elle a la valeur true, indique que la fonction a réussi. L’expression peut être tout ce que l’analyseur d’annotation peut gérer. Les effets des annotations après le retour de la fonction sont applicables uniquement lorsque la fonction est réussie. Cet exemple montre comment `_Success_` interagit avec `_Out_` pour effectuer la bonne chose. Vous pouvez utiliser le mot clé `return` pour représenter la valeur de retour.  
  
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
  
 L’annotation `_Out_` oblige Visual Studio Code analyse à valider que l’appelant passe un pointeur non NULL à une mémoire tampon pour `pInt`, et que la mémoire tampon est initialisée par la fonction avant son retour.  
  
## <a name="sal-best-practice"></a>Meilleures pratiques SAL  
  
### <a name="adding-annotations-to-existing-code"></a>Ajout d’annotations à du code existant  
 SAL est une technologie puissante qui peut vous aider à améliorer la sécurité et la fiabilité de votre code. Une fois que vous avez appris SAL, vous pouvez appliquer les nouvelles compétences à votre travail quotidien. Dans le nouveau code, vous pouvez utiliser les spécifications SAL par conception. dans du code plus ancien, vous pouvez ajouter des annotations de manière incrémentielle et ainsi augmenter les avantages chaque fois que vous mettez à jour.  
  
 Les en-têtes publics Microsoft sont déjà annotés. Par conséquent, dans vos projets, nous vous suggérons d’annoter d’abord les fonctions et fonctions de nœud feuille qui appellent les API Win32 pour tirer le meilleur parti.  
  
### <a name="when-do-i-annotate"></a>Quand dois-je annoter ?  
 Voici quelques recommandations :  
  
- Annotez tous les paramètres de pointeur.  
  
- Annotez les annotations de plage de valeurs pour que l’analyse du code puisse garantir la sécurité des pointeurs et des pointeurs.  
  
- Annotez les règles de verrouillage et le verrouillage des effets secondaires. Pour plus d’informations, consultez [annotation du comportement de verrouillage](../code-quality/annotating-locking-behavior.md).  
  
- Annotez les propriétés de pilote et d’autres propriétés spécifiques au domaine.  
  
  Vous pouvez aussi annoter tous les paramètres pour clarifier votre intention et faciliter la vérification des annotations.  
  
## <a name="related-resources"></a>Ressources connexes  
 [Blog de l’équipe d’analyse du code](https://blogs.msdn.com/b/codeanalysis/)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’annotations SAL pour réduireC++ les erreurs C/code](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Annotation des paramètres de fonction et des valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annoter le comportement](../code-quality/annotating-function-behavior.md) de la fonction   
 [Annoter des structs et des Classes](../code-quality/annotating-structs-and-classes.md)   
 [Annoter le comportement de verrouillage](../code-quality/annotating-locking-behavior.md)   
 [Spécification du moment et de l’endroit où une annotation s’applique](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)
