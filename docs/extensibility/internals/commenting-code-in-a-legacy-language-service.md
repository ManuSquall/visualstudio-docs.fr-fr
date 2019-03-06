---
title: Commentaire du Code dans un Service de langage hérité | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f6b7796ff4bd8f2b37e50e53d58de66f823ef8a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639659"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Code de commentaire dans un service de langage hérité
En général, les langages de programmation fournissent un moyen d’annoter ou de commenter le code. Un commentaire est une section de texte qui fournit des informations supplémentaires sur le code, mais est ignoré pendant la compilation ou une interprétation.

 Les classes de framework (MPF) de package gérée prennent en charge les commentaires et suppression de commentaires dans le texte sélectionné.

## <a name="comment-styles"></a>Styles de commentaire
Il existe deux styles générales de commentaire :

1.  Commentaires sur une ligne où le commentaire se trouve sur une seule ligne.

2.  Commentaires de bloc, où le commentaire peut inclure plusieurs lignes.


Commentaires sur une ligne ont généralement un caractère de début (ou caractères) lors de commentaires de bloc de caractères de début et de fin. Par exemple, en c#, un commentaire sur une ligne commence par `//`, et un commentaire de bloc commence par `/*` et se termine par `*/`.

Lorsque l’utilisateur sélectionne la commande **commenter la sélection** à partir de la **modifier** > **avancé** menu, la commande est acheminée vers le <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> méthode sur le <xref:Microsoft.VisualStudio.Package.Source> classe. Lorsque l’utilisateur sélectionne la commande **Décommenter la sélection**, la commande est acheminée vers le <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> (méthode).

## <a name="support-code-comments"></a>Prise en charge des commentaires de code
 Vous pouvez avoir vos commentaires de code de langue service prise en charge par le biais de la `EnableCommenting` nommé du paramètre de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Cela définit le <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> propriété de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Pour plus d’informations sur la définition des fonctionnalités du service de langage, consultez [inscrire un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md).

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
- [Fonctionnalités de service de langage hérité](../../extensibility/internals/legacy-language-service-features1.md)
- [Inscrire un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)