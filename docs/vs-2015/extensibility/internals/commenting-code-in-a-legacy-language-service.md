---
title: Commentaire du Code dans un Service de langage hérité | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: da04f97cc31ba235fd70aea60f01c51f8c8a2b75
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291900"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Commentaire du code dans un service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En général, les langages de programmation fournissent un moyen d’annoter ou de commenter le code. Un commentaire est une section de texte qui fournit des informations supplémentaires sur le code, mais est ignoré pendant la compilation ou une interprétation.  
  
 Les classes de framework (MPF) de package gérée prennent en charge les commentaires et suppression de commentaires dans le texte sélectionné.  
  
## <a name="comment-styles"></a>Styles de commentaire  
 Il existe deux styles générales de commentaire :  
  
1.  Commentaires sur une ligne où le commentaire se trouve sur une seule ligne.  
  
2.  Commentaires de bloc, où le commentaire peut inclure plusieurs lignes.  
  
 Commentaires sur une ligne ont généralement un caractère de début (ou caractères) lors de commentaires de bloc de caractères de début et de fin. Par exemple, en c#, un commentaire sur une ligne commence par / /, et un commentaire de bloc commence par / * et se termine par \*/.  
  
 Lorsque l’utilisateur sélectionne la commande **commenter la sélection** à partir de la **modifier** -> **avancé** menu, la commande est acheminée vers le <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Source> classe. Lorsque l’utilisateur sélectionne la commande **Décommenter la sélection**, la commande est acheminée vers le <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> (méthode).  
  
## <a name="supporting-code-comments"></a>Prise en charge des commentaires de Code  
 Vous pouvez avoir vos commentaires de code de langue service prise en charge par le biais de la `EnableCommenting` nommé du paramètre de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Cela définit le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> propriété de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Pour plus d’informations sur la définition de langage servicce fonctionnalités, consultez [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Vous devez également substituer la <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> méthode pour retourner un <xref:Microsoft.VisualStudio.Package.CommentInfo> structure avec les caractères de commentaire pour votre langage. C#-caractères de commentaire de ligne de style sont la valeur par défaut.  
  
### <a name="example"></a>Exemple  
 Voici un exemple d’implémentation de la <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> (méthode).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de Service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)   
 [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)

