---
title: Mise en œuvre d’un service linguistique hérité2 Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707673"
---
# <a name="implementing-a-legacy-language-service"></a>Implémentation d’un service de langage hérité
Pour mettre en œuvre un service linguistique à l’aide <xref:Microsoft.VisualStudio.Package.LanguageService> du cadre de forfait géré (MPF), vous devez tirer une classe de la classe et mettre en œuvre les méthodes et propriétés abstraites suivantes :

- Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- La propriété <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Voir les sections appropriées ci-dessous pour plus de détails sur la mise en œuvre de ces méthodes et propriétés.

  Pour prendre en charge d’autres fonctionnalités, votre service linguistique peut devoir tirer une classe de l’une des classes de service linguistique MPF; par exemple, pour prendre en charge des commandes <xref:Microsoft.VisualStudio.Package.ViewFilter> de menu supplémentaires, vous devez tirer <xref:Microsoft.VisualStudio.Package.ViewFilter> une classe de la classe et remplacer plusieurs des méthodes de manutention de commande (voir pour plus de détails). La <xref:Microsoft.VisualStudio.Package.LanguageService> classe fournit un certain nombre de méthodes qui sont appelées à créer de nouveaux instances de différentes classes et vous remplacez la méthode de création appropriée pour fournir un exemple de votre classe. Par exemple, vous devez <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> passer outre <xref:Microsoft.VisualStudio.Package.LanguageService> à la méthode dans <xref:Microsoft.VisualStudio.Package.ViewFilter> la classe pour retourner une instance de votre propre classe. Consultez la section «Classes personnalisées instantanées» pour plus de détails.

  Votre service linguistique peut également fournir ses propres icônes, qui sont utilisées dans de nombreux endroits. Par exemple, lorsqu’une liste d’achèvement IntelliSense est affichée, chaque élément de la liste peut avoir une icône qui lui est associée, marquant l’élément comme méthode, classe, espace de nom, propriété, ou tout ce qui est nécessaire pour votre langue. Ces icônes sont utilisées dans toutes les listes IntelliSense, la **barre de navigation**et dans la fenêtre de tâche Error **List.** Voir la section "Language Service Images" ci-dessous pour plus de détails.

## <a name="getlanguagepreferences-method"></a>Méthode GetLanguagePreferences
 La <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> méthode renvoie toujours <xref:Microsoft.VisualStudio.Package.LanguagePreferences> le même cas d’une classe. Vous pouvez utiliser <xref:Microsoft.VisualStudio.Package.LanguagePreferences> la classe de base si vous n’avez pas besoin de préférences supplémentaires pour votre service linguistique. Les cours de service linguistique MPF supposent la présence d’au moins la classe de base. <xref:Microsoft.VisualStudio.Package.LanguagePreferences>

### <a name="example"></a>Exemple
 Cet exemple montre une <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> mise en œuvre typique de la méthode. Cet exemple utilise <xref:Microsoft.VisualStudio.Package.LanguagePreferences> la classe de base.

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
 Cette méthode renvoie <xref:Microsoft.VisualStudio.Package.IScanner> une instance d’un objet qui implémente un analyseur ou un scanner orienté vers la ligne utilisé pour obtenir des jetons et leurs types et déclencheurs. Ce scanner est <xref:Microsoft.VisualStudio.Package.Colorizer> utilisé dans la classe pour la colorisation bien que le scanner peut également être utilisé pour obtenir des types de jetons et des déclencheurs comme un prélude à une opération d’analyse plus complexe. Vous devez fournir la classe <xref:Microsoft.VisualStudio.Package.IScanner> qui implémente l’interface et vous devez implémenter toutes les méthodes sur l’interface. <xref:Microsoft.VisualStudio.Package.IScanner>

### <a name="example"></a>Exemple
 Cet exemple montre une <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> mise en œuvre typique de la méthode. La `TestScanner` classe implémente l’interface <xref:Microsoft.VisualStudio.Package.IScanner> (non affichée).

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
 Parse le fichier source en fonction d’un certain nombre de raisons différentes. Cette méthode est <xref:Microsoft.VisualStudio.Package.ParseRequest> donnée un objet qui décrit ce qui est attendu d’une opération d’analyse particulière. La <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode invoque un analyseur plus complexe qui détermine la fonctionnalité et la portée des jetons. La <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode est utilisée à l’appui des opérations IntelliSense ainsi que de l’appariement des accolades. Même si vous ne supportez pas ces opérations <xref:Microsoft.VisualStudio.Package.AuthoringScope> avancées, vous devez toujours retourner un <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet valide et cela vous oblige à créer une classe qui implémente l’interface et implémente toutes les méthodes sur cette interface. Vous pouvez retourner des valeurs <xref:Microsoft.VisualStudio.Package.AuthoringScope> nulles de toutes les méthodes, mais l’objet lui-même ne doit pas être une valeur nulle.

### <a name="example"></a>Exemple
 Cet exemple montre une <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> mise en <xref:Microsoft.VisualStudio.Package.AuthoringScope> œuvre minimale de la méthode et de la classe, suffisante pour permettre au service linguistique de compiler et de fonctionner sans réellement prendre en charge aucune des fonctionnalités les plus avancées.

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
 Cette propriété renvoie le nom du service linguistique. Ce doit être le même nom donné lorsque le service linguistique a été enregistré. Ce nom est utilisé dans un certain nombre d’endroits, dont le plus important est la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe où le nom est utilisé pour accéder au registre. Le nom retourné par cette propriété ne doit pas être localisé car il est utilisé dans le registre pour l’entrée du registre et les noms clés.

### <a name="example"></a>Exemple
 Cet exemple montre une <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> mise en œuvre possible de la propriété. Notez que le nom ici est codé dur : le nom réel doit être obtenu à partir d’un fichier de ressources afin qu’il puisse être utilisé dans l’enregistrement d’un service linguistique (voir [Enregistrement d’un service de langue héritée](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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

## <a name="instantiating-custom-classes"></a>Instantané des classes personnalisées
 Les méthodes suivantes dans les classes spécifiées peuvent être remplacées pour fournir des exemples de vos propres versions de chaque classe.

### <a name="in-the-languageservice-class"></a>Dans la classe LanguageService

|Méthode|Classe retournée|Description|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Pour prendre en charge les ajouts personnalisés à la vue de texte.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Pour prendre en charge les propriétés de documents personnalisés.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Pour soutenir la **barre de navigation**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Pour prendre en charge les fonctions dans les modèles d’extrait de code.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Pour prendre en charge les extraits de code (cette méthode n’est généralement pas annulée).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Pour soutenir la <xref:Microsoft.VisualStudio.Package.ParseRequest> personnalisation de la structure (cette méthode n’est généralement pas annulée).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Pour prendre en charge le formatage du code source, la spécalisation des caractères de commentaires et la personnalisation des signatures de méthode.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Pour prendre en charge des commandes de menu supplémentaires.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Pour soutenir la mise en évidence de la syntaxe (cette méthode n’est généralement pas dépassée).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Soutenir l’accès aux préférences linguistiques. Cette méthode doit être mise en œuvre, mais peut retourner une instance de la classe de base.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Fournir un analyseur utilisé pour identifier les types de jetons sur une ligne. Cette méthode doit <xref:Microsoft.VisualStudio.Package.IScanner> être mise en œuvre et doit être dérivée.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Fournir un analyseur utilisé pour identifier les fonctionnalités et la portée dans un fichier source entier. Cette méthode doit être implémentée et <xref:Microsoft.VisualStudio.Package.AuthoringScope> doit retourner une instance de votre version de la classe. Si tout ce que vous voulez prendre <xref:Microsoft.VisualStudio.Package.IScanner> en charge est <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> la mise en évidence syntaxe (qui nécessite <xref:Microsoft.VisualStudio.Package.AuthoringScope> le parser retourné de la méthode), vous ne pouvez rien faire dans cette méthode autre que le retour d’une version de la classe dont les méthodes tous retourner valeurs nulles.|

### <a name="in-the-source-class"></a>Dans la classe Source

|Méthode|Classe retournée|Description|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Pour personnaliser l’affichage des listes d’achèvement IntelliSense (cette méthode n’est généralement pas remplacée).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Pour les marqueurs de soutien dans la liste de tâches error List; spécifiquement, prendre en charge les fonctionnalités au-delà de l’ouverture du fichier et de sauter à la ligne qui a causé l’erreur.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Pour personnaliser l’affichage de IntelliSense Parameter Info ToolTips.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Pour soutenir le code de commentaires.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Pour recueillir des informations pendant l’opération d’analyse.|

### <a name="in-the-authoringscope-class"></a>Dans la classe AuthoringScope

|Méthode|Classe retournée|Description|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Fournit une liste de déclarations telles que les membres ou les types. Cette méthode doit être implémentée, mais peut retourner une valeur nulle. Si cette méthode renvoie un objet valide, l’objet <xref:Microsoft.VisualStudio.Package.Declarations> doit être une instance de votre version de la classe.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Fournit une liste de signatures de méthode pour un contexte donné. Cette méthode doit être implémentée, mais peut retourner une valeur nulle. Si cette méthode renvoie un objet valide, l’objet <xref:Microsoft.VisualStudio.Package.Methods> doit être une instance de votre version de la classe.|

## <a name="language-service-images"></a>Images du service linguistique
 Pour fournir une liste d’icônes à utiliser tout <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> au <xref:Microsoft.VisualStudio.Package.LanguageService> long du <xref:System.Windows.Forms.ImageList> service linguistique, remplacez la méthode dans la classe et retournez une contenant les icônes. La <xref:Microsoft.VisualStudio.Package.LanguageService> classe de base charge un ensemble d’icônes par défaut. Puisque vous spécifiez l’index d’image exact dans les endroits qui ont besoin d’icônes, la façon dont vous arrangez votre propre liste d’images est entièrement à vous.

### <a name="images-used-in-intellisense-completion-lists"></a>Images utilisées dans les listes d’achèvement d’Intellisense
 Pour les listes d’achèvement IntelliSense, l’index d’image est spécifié pour chaque élément de la <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> méthode de la <xref:Microsoft.VisualStudio.Package.Declarations> classe, que vous devez remplacer si vous souhaitez fournir un index d’image. La valeur retournée <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> de la méthode est un <xref:Microsoft.VisualStudio.Package.CompletionSet> index dans la liste d’images fournie <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> au <xref:Microsoft.VisualStudio.Package.LanguageService> constructeur de classe et c’est <xref:Microsoft.VisualStudio.Package.CompletionSet> la même liste <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> d’images retournée de la méthode de la classe (vous pouvez modifier la liste d’images à utiliser pour le si vous remplacez la méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe pour fournir une liste d’images différente).

### <a name="images-used-in-the-navigation-bar"></a>Images utilisées dans la barre de navigation
 La **barre de navigation** affiche des listes de types et de membres et est utilisée pour une navigation rapide peut afficher des icônes. Ces icônes sont obtenues à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> méthode de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe et ne peuvent pas être remplacées spécifiquement pour la barre de **navigation**. Les indices utilisés pour chaque élément dans les combo-boîtes sont spécifiés <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> lorsque les <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> listes représentant les combo-boîtes sont remplies dans la méthode de la classe (voir [Support for the Navigation Bar in a Legacy Language Service](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Ces indices d’image sont obtenus en quelque sorte à <xref:Microsoft.VisualStudio.Package.Declarations> partir du parseur, généralement à travers votre version de la classe. La façon dont les indices sont obtenus dépend entièrement de vous.

### <a name="images-used-in-the-error-list-task-window"></a>Images utilisées dans la fenêtre de tâche de liste d’erreurs
 Chaque <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> fois que le analyseur de méthode (voir [Legacy Language Service Parser et Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) rencontre une erreur et transmet cette erreur à la <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> méthode de la <xref:Microsoft.VisualStudio.Package.AuthoringSink> classe, l’erreur est signalée dans la fenêtre de tâche de la liste **d’erreurs.** Une icône peut être associée à chaque élément qui apparaît dans la fenêtre <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> de tâche <xref:Microsoft.VisualStudio.Package.LanguageService> et cette icône provient de la même liste d’images retournée de la méthode de la classe. Le comportement par défaut des classes MPF est de ne pas afficher une image avec le message d’erreur. Cependant, vous pouvez passer outre à ce comportement <xref:Microsoft.VisualStudio.Package.Source> en dérivant <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> une classe de la classe et en l’écartant de la méthode. Dans cette méthode, vous <xref:Microsoft.VisualStudio.Package.DocumentTask> créez un nouvel objet. Avant de retourner cet objet, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> propriété sur l’objet <xref:Microsoft.VisualStudio.Package.DocumentTask> pour définir l’index d’image. Cela ressemblerait à l’exemple suivant. Notez `TestIconImageIndex` qu’il s’agit d’un recensement qui répertorie toutes les icônes et qui est spécifique à cet exemple. Vous pouvez avoir une façon différente d’identifier les icônes dans votre service linguistique.

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

## <a name="the-default-image-list-for-a-language-service"></a>La liste d’images par défaut pour un service linguistique
 La liste d’images par défaut fournie avec les classes de service linguistique MPF de base contient un certain nombre d’icônes associées aux éléments linguistiques les plus courants. La majeure partie de ces icônes sont disposées en ensembles de six variantes, correspondant aux concepts d’accès du public, interne, ami, protégé, privé et raccourci. Par exemple, vous pouvez avoir différentes icônes pour une méthode selon qu’elle est publique, protégée ou privée.

 L’énumération suivante spécifie les noms typiques de chaque ensemble d’icônes et spécifie l’index associé. Par exemple, en fonction de l’énumération, vous pouvez `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`spécifier l’indice d’image d’une méthode protégée comme . Vous pouvez changer les noms dans cette énumération comme désiré.

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
