---
title: Implémentation d’un Service2 de langage hérité | Microsoft Docs
description: Découvrez comment implémenter un service de langage hérité qui prend en charge les fonctionnalités du service de langage étendu, à l’aide de Managed package Framework (MPF). Partie 2 sur 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fca2548ddb0c8281241b14de0ec470cfe22db1a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900120"
---
# <a name="implementing-a-legacy-language-service-2"></a>Implémentation d’un service de langage hérité 2
Pour implémenter un service de langage à l’aide de Managed package Framework (MPF), vous devez dériver une classe de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe et implémenter les méthodes et propriétés abstraites suivantes :

- Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- La propriété <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Pour plus d’informations sur l’implémentation de ces méthodes et propriétés, consultez les sections appropriées ci-dessous.

  Pour prendre en charge des fonctionnalités supplémentaires, votre service de langage peut avoir à dériver une classe de l’une des classes de service de langage MPF ; par exemple, pour prendre en charge des commandes de menu supplémentaires, vous devez dériver une classe de la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe et substituer plusieurs méthodes de gestion des commandes (consultez <xref:Microsoft.VisualStudio.Package.ViewFilter> pour plus d’informations). La <xref:Microsoft.VisualStudio.Package.LanguageService> classe fournit un certain nombre de méthodes qui sont appelées pour créer de nouvelles instances de différentes classes et vous substituez la méthode de création appropriée pour fournir une instance de votre classe. Par exemple, vous devez substituer la <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe pour retourner une instance de votre propre <xref:Microsoft.VisualStudio.Package.ViewFilter> classe. Pour plus d’informations, consultez la section « instanciation de classes personnalisées ».

  Votre service de langage peut également fournir ses propres icônes, qui sont utilisées à de nombreux endroits. Par exemple, lorsqu’une liste de saisie semi-automatique IntelliSense est affichée, chaque élément de la liste peut être associé à une icône, en marquant l’élément comme une méthode, une classe, un espace de noms, une propriété ou tout ce qui est nécessaire pour votre langage. Ces icônes sont utilisées dans toutes les listes IntelliSense, la **barre de navigation** et dans la fenêtre de tâche **liste d’erreurs** . Pour plus d’informations, consultez la section « images du service de langage » ci-dessous.

## <a name="getlanguagepreferences-method"></a>Méthode GetLanguagePreferences
 La <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> méthode retourne toujours la même instance d’une <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Vous pouvez utiliser la classe de base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> si vous n’avez pas besoin de préférences supplémentaires pour votre service de langage. Les classes du service de langage MPF supposent la présence d’au moins la classe de base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

### <a name="example"></a>Exemple
 Cet exemple montre une implémentation classique de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> méthode. Cet exemple utilise la classe de base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>Méthode GetScanner
 Cette méthode retourne une instance d’un <xref:Microsoft.VisualStudio.Package.IScanner> objet qui implémente un analyseur orienté ligne ou un scanneur utilisé pour obtenir des jetons et leurs types et déclencheurs. Ce scanneur est utilisé dans la <xref:Microsoft.VisualStudio.Package.Colorizer> classe pour la colorisation même si le scanneur peut également être utilisé pour obtenir des types de jetons et des déclencheurs comme préambule destiné à à une opération d’analyse plus complexe. Vous devez fournir la classe qui implémente l' <xref:Microsoft.VisualStudio.Package.IScanner> interface et vous devez implémenter toutes les méthodes sur l' <xref:Microsoft.VisualStudio.Package.IScanner> interface.

### <a name="example"></a>Exemple
 Cet exemple montre une implémentation classique de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> méthode. La `TestScanner` classe implémente l' <xref:Microsoft.VisualStudio.Package.IScanner> interface (non illustrée).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>Méthode ParseSource
 Analyse le fichier source en fonction de plusieurs raisons. Cette méthode reçoit un <xref:Microsoft.VisualStudio.Package.ParseRequest> objet qui décrit ce qui est attendu à partir d’une opération d’analyse particulière. La <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode appelle un analyseur plus complexe qui détermine la fonctionnalité et la portée des jetons. La <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode est utilisée pour la prise en charge des opérations IntelliSense et de la correspondance des accolades. Même si vous ne prenez pas en charge ces opérations avancées, vous devez toujours retourner un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet valide et vous obliger à créer une classe qui implémente l' <xref:Microsoft.VisualStudio.Package.AuthoringScope> interface et à implémenter toutes les méthodes sur cette interface. Vous pouvez retourner des valeurs NULL à partir de toutes les méthodes, mais l' <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet lui-même ne doit pas être une valeur null.

### <a name="example"></a>Exemple
 Cet exemple montre une implémentation minimale de la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode et de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe, suffisante pour permettre au service de langage de se compiler et de fonctionner sans réellement prendre en charge les fonctionnalités les plus avancées.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Propriété Name
 Cette propriété retourne le nom du service de langage. Il doit s’agir du même nom que celui indiqué lors de l’inscription du service de langage. Ce nom est utilisé à plusieurs endroits, le plus important étant la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe où le nom est utilisé pour accéder au registre. Le nom retourné par cette propriété ne doit pas être localisé, car il est utilisé dans le registre pour les noms d’entrée et de clé de registre.

### <a name="example"></a>Exemple
 Cet exemple illustre une implémentation possible de la <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> propriété. Notez que le nom est codé en dur : le nom réel doit être obtenu à partir d’un fichier de ressources pour pouvoir être utilisé lors de l’inscription d’un service de langage (consultez [inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>Instanciation de classes personnalisées
 Les méthodes suivantes dans les classes spécifiées peuvent être substituées pour fournir des instances de vos propres versions de chaque classe.

### <a name="in-the-languageservice-class"></a>Dans la classe LanguageService

|Méthode|Classe retournée|Description|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Pour prendre en charge les ajouts personnalisés à l’affichage de texte.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Pour prendre en charge les propriétés de document personnalisées.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Pour prendre en charge la **barre de navigation**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Pour prendre en charge les fonctions dans les modèles d’extraits de code.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Pour prendre en charge les extraits de code (cette méthode n’est généralement pas substituée).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Pour prendre en charge la personnalisation de la <xref:Microsoft.VisualStudio.Package.ParseRequest> structure (cette méthode n’est généralement pas substituée).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Pour prendre en charge le formatage du code source, la spécification des caractères de commentaire et la personnalisation des signatures de méthode.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Pour prendre en charge des commandes de menu supplémentaires.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Pour prendre en charge la mise en surbrillance syntaxique (cette méthode n’est généralement pas substituée).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Pour prendre en charge l’accès aux préférences linguistiques. Cette méthode doit être implémentée, mais peut retourner une instance de la classe de base.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Pour fournir un analyseur utilisé pour identifier les types de jetons sur une ligne. Cette méthode doit être implémentée et <xref:Microsoft.VisualStudio.Package.IScanner> doit être dérivée de.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Pour fournir un analyseur utilisé pour identifier les fonctionnalités et l’étendue dans l’ensemble d’un fichier source. Cette méthode doit être implémentée et doit retourner une instance de votre version de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. Si tout ce que vous voulez prendre en charge est la mise en surbrillance de la syntaxe (qui requiert l' <xref:Microsoft.VisualStudio.Package.IScanner> analyseur retourné par la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> méthode), vous pouvez ne rien faire dans cette méthode que retourner une version de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe dont les méthodes retournent toutes des valeurs NULL.|

### <a name="in-the-source-class"></a>Dans la classe source

|Méthode|Classe retournée|Description|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Pour personnaliser l’affichage des listes de saisie semi-automatique IntelliSense (cette méthode n’est généralement pas substituée).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Pour les marqueurs de prise en charge dans la liste des tâches Liste d’erreurs ; plus précisément, la prise en charge des fonctionnalités au-delà de l’ouverture du fichier et de l’accès à la ligne à l’origine de l’erreur.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Pour personnaliser l’affichage des info-bulles des informations sur les paramètres IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Pour prendre en charge le code de commentaires.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Pour collecter des informations pendant l’opération d’analyse.|

### <a name="in-the-authoringscope-class"></a>Dans la classe AuthoringScope

|Méthode|Classe retournée|Description|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Fournit une liste de déclarations, telles que des membres ou des types. Cette méthode doit être implémentée, mais peut retourner une valeur null. Si cette méthode retourne un objet valide, l’objet doit être une instance de votre version de la <xref:Microsoft.VisualStudio.Package.Declarations> classe.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Fournit la liste des signatures de méthode pour un contexte donné. Cette méthode doit être implémentée, mais peut retourner une valeur null. Si cette méthode retourne un objet valide, l’objet doit être une instance de votre version de la <xref:Microsoft.VisualStudio.Package.Methods> classe.|

## <a name="language-service-images"></a>Images du service de langage
 Pour fournir une liste d’icônes à utiliser dans le service de langage, substituez la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe et retournez une <xref:System.Windows.Forms.ImageList> contenant les icônes. La <xref:Microsoft.VisualStudio.Package.LanguageService> classe de base charge un ensemble d’icônes par défaut. Étant donné que vous spécifiez l’index d’images exact dans les emplacements qui nécessitent des icônes, la façon dont vous organisez votre propre liste d’images dépend entièrement de vous.

### <a name="images-used-in-intellisense-completion-lists"></a>Images utilisées dans les listes de saisie semi-automatique IntelliSense
 Pour les listes de saisie semi-automatique IntelliSense, l’index d’image est spécifié pour chaque élément de la <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> méthode de la <xref:Microsoft.VisualStudio.Package.Declarations> classe, que vous devez substituer si vous souhaitez fournir un index d’image. La valeur retournée par la <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> méthode est un index dans la liste d’images fournie au <xref:Microsoft.VisualStudio.Package.CompletionSet> constructeur de classe et qui est la même liste d’images retournée à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe (vous pouvez modifier la liste d’images à utiliser pour le <xref:Microsoft.VisualStudio.Package.CompletionSet> si vous substituez la <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe pour fournir une liste d’images différente).

### <a name="images-used-in-the-navigation-bar"></a>Images utilisées dans la barre de navigation
 La **barre de navigation** affiche des listes de types et de membres, et est utilisée pour la navigation rapide peut afficher des icônes. Ces icônes sont obtenues à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe et ne peuvent pas être substituées spécifiquement pour la **barre de navigation**. Les index utilisés pour chaque élément dans les zones de liste déroulante sont spécifiés quand les listes représentant les zones de liste déroulante sont remplies dans la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe (consultez [prise en charge de la barre de navigation dans un service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Ces index d’image sont obtenus à partir de l’analyseur, généralement par le biais de votre version de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. La façon dont les index sont obtenus dépend entièrement de vous.

### <a name="images-used-in-the-error-list-task-window"></a>Images utilisées dans la fenêtre de tâche Liste d’erreurs
 Chaque fois que l' <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode (Voir l’analyseur [et le scanneur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) rencontre une erreur et passe cette erreur à la <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe, l’erreur est signalée dans la fenêtre de tâche **liste d’erreurs** . Une icône peut être associée à chaque élément qui s’affiche dans la fenêtre de tâche et cette icône provient de la même liste d’images retournée par la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Le comportement par défaut des classes MPF consiste à ne pas afficher d’image avec le message d’erreur. Toutefois, vous pouvez substituer ce comportement en dérivant une classe de la <xref:Microsoft.VisualStudio.Package.Source> classe et en substituant la <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> méthode. Dans cette méthode, vous créez un nouvel <xref:Microsoft.VisualStudio.Package.DocumentTask> objet. Avant de retourner cet objet, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> propriété sur l' <xref:Microsoft.VisualStudio.Package.DocumentTask> objet pour définir l’index d’image. Cela devrait ressembler à l’exemple suivant. Notez que `TestIconImageIndex` est une énumération qui répertorie toutes les icônes et qui est spécifique à cet exemple. Vous pouvez avoir une autre façon d’identifier les icônes dans votre service de langage.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>Liste d’images par défaut pour un service de langage
 La liste d’images par défaut fournie avec les classes de service de langage MPF de base contient un certain nombre d’icônes associées aux éléments de langage les plus courants. La plupart de ces icônes sont organisées en ensembles de six variations, correspondant aux concepts d’accès public, Internal, Friend, protected, Private et shortcut. Par exemple, vous pouvez avoir différentes icônes pour une méthode selon qu’elle est publique, protégée ou privée.

 L’énumération suivante spécifie des noms typiques pour chaque jeu d’icônes et spécifie l’index associé. Par exemple, en fonction de l’énumération, vous pouvez spécifier l’index d’image pour une méthode protégée en tant que `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . Vous pouvez modifier les noms dans cette énumération comme vous le souhaitez.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>Voir aussi
- [Implémentation d’un service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Présentation du service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)
- [Inscription d’un service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
