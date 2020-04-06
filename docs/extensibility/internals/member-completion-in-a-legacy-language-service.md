---
title: Achèvement des membres dans un service de langue héritée (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707199"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Saisie semi-automatique de membre dans un service de langage hérité

L’achèvement des membres IntelliSense est un conseil d’outil qui affiche une liste de membres possibles d’une portée particulière comme une classe, une structure, un recensement ou un espace de nom. Par exemple, dans le C, si l’utilisateur tape « ceci » suivi d’une période, une liste de tous les membres de la classe ou de la structure à la portée actuelle est présentée dans une liste à partir de laquelle l’utilisateur peut sélectionner.

Le cadre de paquet géré (MPF) fournit un soutien à la pointe de l’outil et la gestion de la liste dans la pointe de l’outil; tout ce qu’il faut, c’est la coopération du parse-à-dire pour fournir les données qui apparaissent dans la liste.

Les services linguistiques hérités sont mis en œuvre dans le cadre d’un VSPackage, mais la nouvelle façon de mettre en œuvre des fonctionnalités de service linguistique est d’utiliser des extensions MEF. Pour en savoir plus, voir [Extending the Editor and Language Services](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Nous vous recommandons de commencer à utiliser le nouvel éditeur API dès que possible. Cela améliorera les performances de votre service linguistique et vous permettra de profiter des nouvelles fonctionnalités de l’éditeur.

## <a name="how-it-works"></a>Fonctionnement

Voici les deux façons dont une liste de membres est affichée à l’aide des classes MPF :

- Positionnement de la caret sur un identifiant ou après un personnage d’achèvement du membre et sélection des **membres de** liste du menu **IntelliSense.**

- Le <xref:Microsoft.VisualStudio.Package.IScanner> scanner détecte un caractère d’achèvement du membre et définit un déclencheur symbolique de [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) pour ce personnage.

Un caractère d’achèvement des membres indique qu’un membre d’une classe, d’une structure ou d’un recensement doit suivre. Par exemple, dans C ou Visual Basic, `.`le personnage d’achèvement du `.` membre `->`est un , tandis que dans C , le personnage est soit a ou a . La valeur de déclenchement est définie lorsque le personnage choisi par le membre est numérisé.

### <a name="the-intellisense-member-list-command"></a>Le Commandement de la liste des membres d’IntelliSense

La <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> commande lance un <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> appel à <xref:Microsoft.VisualStudio.Package.Source> la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode sur la classe <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> et la méthode, à son tour, appelle le analyseur de méthode avec la raison d’analyse de [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Le parseur détermine le contexte de la position actuelle ainsi que le jeton sous ou immédiatement avant la position actuelle. Sur la base de ce jeton, une liste de déclarations est présentée. Par exemple, en C, si vous placez le caret sur un membre de la classe et sélectionnez **les membres de la Liste,** vous obtenez une liste de tous les membres de la classe. Si vous positionnez le caret après une période qui suit une variable d’objet, vous obtenez une liste de tous les membres de la classe que représente l’objet. Notez que si le caret est placé sur un membre lorsque la liste des membres est affichée, la sélection d’un membre de la liste remplace le membre, le caret est sur celui de la liste.

### <a name="the-token-trigger"></a>Le déclencheur symbolique

Le [déclencheur TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) lance un <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> appel <xref:Microsoft.VisualStudio.Package.Source> à la <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> méthode sur la classe et la méthode, à son tour, appelle le parser avec la raison de parse de [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Si le déclencheur symbolique comprenait également le drapeau [TokenTriggers.MatchBraces,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) la raison de l’analyse est [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), qui combine la sélection des membres et la mise en évidence accolade.

Le analyseur détermine le contexte de la position actuelle ainsi que ce qui a été tapé avant que le personnage choisi par le membre ne s’adresse. À partir de ces informations, le parseur crée une liste de tous les membres de la portée demandée. Cette liste de déclarations <xref:Microsoft.VisualStudio.Package.AuthoringScope> est stockée dans <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> l’objet qui est retourné de la méthode. Si des déclarations sont retournées, le conseil de l’outil d’achèvement du membre est affiché. La pointe de l’outil <xref:Microsoft.VisualStudio.Package.CompletionSet> est gérée par un exemple de la classe.

## <a name="enable-support-for-member-completion"></a>Permettre le soutien à l’achèvement des membres

Vous devez `CodeSense` avoir l’entrée de registre réglée à 1 pour soutenir toute opération IntelliSense. Cette inscription au registre peut être définie <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> avec un paramètre désigné transmis à l’attribut utilisateur associé à l’ensemble de langue. Les cours de service linguistique lisent <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> la valeur <xref:Microsoft.VisualStudio.Package.LanguagePreferences> de cette entrée de registre à partir de la propriété sur la classe.

Si votre scanner renvoie le déclencheur symbolique de [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>), et votre analyseur renvoie une liste de déclarations, alors la liste d’achèvement des membres est affichée.

## <a name="support-member-completion-in-the-scanner"></a>Soutenir l’achèvement des membres dans le scanner

Le scanner doit être en mesure de détecter un personnage d’achèvement du membre et de définir le déclencheur symbolique de [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) lorsque ce personnage est analysé.

### <a name="scanner-example"></a>Exemple de scanner

Voici un exemple simplifié de détection du caractère <xref:Microsoft.VisualStudio.Package.TokenTriggers> d’achèvement du membre et de réglage du drapeau approprié. Cet exemple n’est qu’à des fins illustratives. Il suppose que votre scanner `GetNextToken` contient une méthode qui identifie et renvoie les jetons à partir d’une ligne de texte. Le code d’exemple définit simplement la gâchette chaque fois qu’il voit le bon type de caractère.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char memberSelectChar = '.';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (c == memberSelectChar)
                {
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;
                }
            }
            return foundToken;
        }
    }
}
```

## <a name="support-member-completion-in-the-parser"></a>Soutien à l’achèvement des membres dans le Parser

Pour l’achèvement <xref:Microsoft.VisualStudio.Package.Source> des <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> membres, le groupe appelle la méthode. Vous devez implémenter la liste <xref:Microsoft.VisualStudio.Package.Declarations> dans une classe dérivée de la classe. Consultez <xref:Microsoft.VisualStudio.Package.Declarations> le cours pour plus de détails sur les méthodes que vous devez mettre en œuvre.

Le parser est appelé avec [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) ou [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) quand un personnage choisi par membre est tapé. L’emplacement donné <xref:Microsoft.VisualStudio.Package.ParseRequest> dans l’objet est immédiatement après que le personnage choisi par le membre. Le parseur doit recueillir les noms de tous les membres qui peuvent apparaître dans une liste de membres à ce point particulier dans le code source. Ensuite, le parseur doit analyser la ligne actuelle pour déterminer la portée que l’utilisateur veut associée au personnage choisi par le membre.

Cette portée est basée sur le type d’identifiant avant que le personnage choisi par le membre. Par exemple, dans C, étant `languageService` donné la `LanguageService`variable du membre qui a un type de , tapant **languageService.** produit une liste de tous `LanguageService` les membres de la classe. Également en C, en tapant **ceci.** produit une liste de tous les membres de la classe dans la portée actuelle.

### <a name="parser-example"></a>Exemple de Parser

L’exemple suivant montre une <xref:Microsoft.VisualStudio.Package.Declarations> façon de remplir une liste. Ce code suppose que le parseur construit une déclaration et `AddDeclaration` l’ajoute `TestAuthoringScope` à la liste en appelant une méthode sur la classe.

```csharp
using System.Collections;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclaration
    {
        public string Name;            // Name of declaration
        public int     TypeImageIndex; // Glyph index
        public string Description;     // Description of declaration

        public TestDeclaration(string name, int typeImageIndex, string description)
        {
            this.Name = name;
            this.TypeImageIndex = typeImageIndex;
            this.Description = description;
        }
    }

    //===================================================
    internal class TestDeclarations : Declarations
    {
        private ArrayList declarations;

        public TestDeclarations()
            : base()
        {
            declarations = new ArrayList();
        }

        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        //////////////////////////////////////////////////////////////////////
        // Declarations of class methods that must be implemented.
        public override int GetCount()
        {
            // Return the number of declarations to show.
            return declarations.Count;
        }

        public override string GetDescription(int index)
        {
            // Return the description of the specified item.
            string description = "";
            if (index >= 0 && index < declarations.Count)
            {
                description = ((TestDeclaration)declarations[index]).Description;
            }
            return description;
        }

        public override string GetDisplayText(int index)
        {
            // Determine what is displayed in the tool tip list.
            string text = null;
            if (index >= 0 && index < declarations.Count)
            {
                text = ((TestDeclaration)declarations[index]).Name;
            }
            return text;
        }

        public override int GetGlyph(int index)
        {
            // Return index of image to display next to the display text.
            int imageIndex = -1;
            if (index >= 0 && index < declarations.Count)
            {
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;
            }
            return imageIndex;
        }

        public override string GetName(int index)
        {
            string name = null;
            if (index >= 0 && index < declarations.Count)
            {
                name = ((TestDeclaration)declarations[index]).Name;
            }
            return name;
        }
    }

    //===================================================
    public class TestAuthoringScope : AuthoringScope
    {
        private TestDeclarations declarationsList;

        public void AddDeclaration(TestDeclaration declaration)
        {
            if (declaration != null)
            {
                if (declarationsList == null)
                {
                    declarationsList = new TestDeclarations();
                }
                declarationsList.AddDeclaration(declaration);
            }
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return declarationsList;
        }

        /////////////////////////////////////////////////
        // Remainder of AuthoringScope methods not shown.
        /////////////////////////////////////////////////
    }

    //===================================================
    class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            TestAuthoringScope scope = new TestAuthoringScope();
            if (req.Reason == ParseReason.MemberSelect ||
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)
            {
                // Gather list of declarations based on what the user
                // has typed so far. In this example, this list is an array of
                // MemberDeclaration objects (a helper class you might implement
                // to hold member declarations).
                // How this list is gathered is dependent on the parser
                // and is not shown here.
                MemberDeclarations memberDeclarations;
                memberDeclarations = GetDeclarationsForScope();

                // Now populate the Declarations list in the authoring scope.
                // GetImageIndexBasedOnType() is a helper method you
                // might implement to convert a member type to an index into
                // the image list returned from the language service.
                foreach (MemberDeclaration dec in memberDeclarations)
                {
                    scope.AddDeclaration(new TestDeclaration(
                                             dec.Name,
                                             GetImageIndexBasedOnType(dec.Type),
                                             dec.Description));
                }
            }
            return scope;
        }
    }
}
```
