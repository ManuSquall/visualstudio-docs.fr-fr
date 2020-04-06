---
title: Code de commentaires dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709437"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Code de commentaires dans un service linguistique hérité
Les langages de programmation fournissent généralement un moyen d’annoter ou de commenter le code. Un commentaire est une section de texte qui fournit des informations supplémentaires sur le code, mais est ignorée lors de la compilation ou de l’interprétation.

 Les classes de cadre de paquets gérés (MPF) fournissent un soutien pour commenter et désengagementer le texte sélectionné.

## <a name="comment-styles"></a>Styles de commentaires
Il existe deux styles généraux de commentaires :

1. Commentaires de ligne, où le commentaire est sur une seule ligne.

2. Bloquer les commentaires, où le commentaire peut inclure plusieurs lignes.

Les commentaires en ligne ont généralement un caractère de départ (ou des caractères), tandis que les commentaires de bloc ont à la fois des caractères de début et de fin. Par exemple, dans C, un `//`commentaire de ligne commence `/*` par `*/`, et un commentaire de bloc commence par et se termine par .

Lorsque l’utilisateur sélectionne la **sélection de commentaire** de commande dans le menu **Edit** > **Advanced,** la commande est acheminée vers la <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> méthode de la <xref:Microsoft.VisualStudio.Package.Source> classe. Lorsque l’utilisateur sélectionne la commande **Uncomment Selection**, <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> la commande est acheminée vers la méthode.

## <a name="support-code-comments"></a>Commentaires de code de support
 Vous pouvez avoir vos commentaires de code `EnableCommenting` de support <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> de service linguistique au moyen du paramètre nommé de la . Cela définit <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> propriété de la classe. Pour plus d’informations sur l’établissement des fonctionnalités du service linguistique, consultez [Register a legacy language service](../../extensibility/internals/registering-a-legacy-language-service1.md).

 Vous devez également <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> passer outre <xref:Microsoft.VisualStudio.Package.CommentInfo> à la méthode pour retourner une structure avec les caractères de commentaire pour votre langue. Les caractères de commentaires en ligne de style C sont par défaut.

### <a name="example"></a>Exemple
 Voici un exemple de <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> mise en œuvre de la méthode.

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
- [Caractéristiques du service linguistique hérité](../../extensibility/internals/legacy-language-service-features1.md)
- [Enregistrer un service linguistique hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)
