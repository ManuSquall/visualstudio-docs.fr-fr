---
title: Implémentation d’un langage hérité2 | Microsoft Docs
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
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1fb00e995e1a684438e99428437b4bca1069b970
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831378"
---
# <a name="implementing-a-legacy-language-service"></a>Implémentation d’un Service de langage hérité
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pour implémenter un service de langage à l’aide de l’infrastructure de package managé (MPF), vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService> classe et implémenter les méthodes abstraites suivantes et les propriétés :  
  
- Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>   
  
- Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
- Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
- La propriété <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>  
  
  Consultez les sections appropriées ci-dessous pour plus d’informations sur l’implémentation de ces méthodes et propriétés.  
  
  Pour prendre en charge des fonctionnalités supplémentaires, votre service de langage peut avoir à dériver une classe d’une des classes de service de langage MPF ; par exemple, pour prendre en charge les commandes de menu supplémentaires, vous devez dériver une classe à partir de la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe et remplacer plusieurs de la commande de gestion des méthodes (voir <xref:Microsoft.VisualStudio.Package.ViewFilter> pour plus d’informations). Le <xref:Microsoft.VisualStudio.Package.LanguageService> classe fournit plusieurs méthodes qui sont appelées pour créer des instances de différentes classes et vous remplacez la méthode de création approprié pour fournir une instance de votre classe. Par exemple, vous devez remplacer le <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.LanguageService> classe pour retourner une instance de votre propre <xref:Microsoft.VisualStudio.Package.ViewFilter> classe. Consultez la section « Instanciation des Classes personnalisées » pour plus d’informations.  
  
  Votre service de langage peut également fournir ses propres icônes, qui sont utilisés dans de nombreux endroits. Par exemple, lorsqu’une liste de saisie semi-automatique IntelliSense s’affiche, chaque élément dans la liste peut avoir une icône associée, marquer l’élément comme une méthode de classe, espace de noms, propriété, ou ce qui est nécessaire pour votre langue. Ces icônes sont utilisées dans toutes les listes IntelliSense, la **barre de Navigation**, puis, dans le **liste d’erreurs** fenêtre des tâches. Consultez la section « Images du Service de langage » ci-dessous pour plus d’informations.  
  
## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences (méthode)  
 Le <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> méthode retourne toujours la même instance d’un <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Vous pouvez utiliser la base de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe si vous n’avez pas besoin d’aucune des préférences supplémentaires pour votre service de langage. Les classes de service de langage MPF supposent la présence d’au moins la base de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre une implémentation classique de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> (méthode). Cet exemple utilise la base de <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
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
  
## <a name="getscanner-method"></a>GetScanner (méthode)  
 Cette méthode retourne une instance d’un <xref:Microsoft.VisualStudio.Package.IScanner> objet qui implémente un analyseur orienté ligne ou l’analyseur utilisé pour obtenir des jetons et leurs types et des déclencheurs. Ce scanneur est utilisé dans le <xref:Microsoft.VisualStudio.Package.Colorizer> classe pour la colorisation, bien que le scanneur peut également être utilisé pour obtenir les types de jetons et les déclencheurs comme un prélude à une opération d’analyse plus complexe. Vous devez fournir la classe qui implémente le <xref:Microsoft.VisualStudio.Package.IScanner> interface et que vous devez implémenter toutes les méthodes sur le <xref:Microsoft.VisualStudio.Package.IScanner> interface.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre une implémentation classique de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (méthode). Le `TestScanner` la classe implémente le <xref:Microsoft.VisualStudio.Package.IScanner> interface (non illustré).  
  
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
  
## <a name="parsesource-method"></a>ParseSource (méthode)  
 Analyse le fichier source selon un certain nombre de raisons. Cette méthode reçoit un <xref:Microsoft.VisualStudio.Package.ParseRequest> objet qui décrit ce qui est attendu à partir d’une opération d’analyse spécifique. Le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode appelle un analyseur plus complexe qui détermine la fonctionnalité du jeton et l’étendue. Le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> méthode est utilisée dans la prise en charge pour les opérations IntelliSense, ainsi que la correspondance des accolades. Même si vous ne gèrent pas ces opérations avancées, vous devez retourner encore valide <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet et qui vous oblige à créer une classe qui implémente le <xref:Microsoft.VisualStudio.Package.AuthoringScope> interface et implémenter toutes les méthodes sur cette interface. Vous pouvez retourner des valeurs null à partir de toutes les méthodes, mais le <xref:Microsoft.VisualStudio.Package.AuthoringScope> objet lui-même ne doit pas être une valeur null.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre une implémentation minimale de la <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (méthode) et le <xref:Microsoft.VisualStudio.Package.AuthoringScope> (classe), suffisante pour permettre au service de langage compiler et fonctionner sans réellement prenant en charge les fonctionnalités plus avancées.  
  
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
 Cette propriété retourne le nom du service de langage. Cela doit être le même nom donné lorsque le service de langage a été inscrit. Ce nom est utilisé dans plusieurs emplacements, dont le plus important est le <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe où le nom est utilisé pour accéder au Registre. Le nom retourné par cette propriété ne doit pas être localisé car il est utilisé dans le Registre pour l’entrée de Registre et les noms de clé.  
  
### <a name="example"></a>Exemple  
 Cet exemple montre une implémentation possible du <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> propriété. Notez que le nom ici est codé en dur : le nom réel doit être obtenu à partir d’un fichier de ressources afin qu’il peut être utilisé dans l’inscription d’un service de langage (consultez [l’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
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
  
## <a name="instantiating-custom-classes"></a>Lors de l’instanciation de Classes personnalisées  
 Les méthodes suivantes dans les classes spécifiées peuvent être substituées pour fournir des instances de vos propres versions de chaque classe.  
  
### <a name="in-the-languageservice-class"></a>Dans la classe LanguageService  
  
|Méthode|Classe retournée|Description|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Pour prendre en charge les ajouts personnalisés à l’affichage de texte.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Pour prendre en charge les propriétés de document personnalisées.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Pour prendre en charge la **barre de Navigation**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Pour prendre en charge les fonctions dans les modèles d’extrait de code.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Pour prendre en charge des extraits de code (cette méthode n’est généralement pas remplacée).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Pour prendre en charge la personnalisation de la <xref:Microsoft.VisualStudio.Package.ParseRequest> structure (cette méthode n’est généralement pas remplacée).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Pour prendre en charge la mise en forme code source, en spécifiant des caractères de commentaire et la personnalisation des signatures de méthode.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Pour prendre en charge les commandes de menu supplémentaires.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Pour prendre en charge la coloration syntaxique (cette méthode n’est généralement pas remplacée).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Pour prendre en charge les accès aux préférences de langue. Cette méthode doit être implémentée, mais peut retourner une instance de la classe de base.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Pour fournir un analyseur utilisé pour identifier les types de jetons sur une ligne. Cette méthode doit être implémentée et <xref:Microsoft.VisualStudio.Package.IScanner> doit être dérivé.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Pour fournir un analyseur utilisé pour identifier les fonctionnalités et l’étendue tout au long d’un fichier source entier. Cette méthode doit être implémentée et doit retourner une instance de votre version de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe. Si tout ce que vous souhaitez prendre en charge est la coloration syntaxique (ce qui nécessite le <xref:Microsoft.VisualStudio.Package.IScanner> analyseur retourné à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> (méthode)), vous pouvez ne rien faire dans cette méthode autre que de retourner une version de la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe dont toutes les méthodes retournent des valeurs null.|  
  
### <a name="in-the-source-class"></a>Dans la classe Source  
  
|Méthode|Classe retournée|Description|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Pour personnaliser l’affichage des listes de saisie semi-automatique IntelliSense (cette méthode n’est généralement pas remplacée).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Pour prendre en charge des marqueurs dans la liste des tâches liste d’erreurs ; plus précisément, prise en charge des fonctionnalités au-delà de l’ouverture du fichier et accéder à la ligne qui a provoqué l’erreur.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Pour personnaliser l’affichage des info-bulles des informations de paramètre IntelliSense.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Pour prendre en charge les commentaires de code.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Pour rassembler des informations pendant l’opération d’analyse.|  
  
### <a name="in-the-authoringscope-class"></a>Dans la classe AuthoringScope  
  
|Méthode|Classe retournée|Description|  
|------------|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Fournit une liste des déclarations telles que les membres ou types. Cette méthode doit être implémentée, mais peut retourner une valeur null. Si cette méthode retourne un objet valide, l’objet doit être une instance de votre version de la <xref:Microsoft.VisualStudio.Package.Declarations> classe.|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Fournit une liste de signatures de méthode pour un contexte donné. Cette méthode doit être implémentée, mais peut retourner une valeur null. Si cette méthode retourne un objet valide, l’objet doit être une instance de votre version de la <xref:Microsoft.VisualStudio.Package.Methods> classe.|  
  
## <a name="language-service-images"></a>Images de Service de langage  
 Pour fournir une liste d’icônes à utiliser dans le service de langage, substituez le <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.LanguageService> classe et de retourner un <xref:System.Windows.Forms.ImageList> contenant les icônes. La base de <xref:Microsoft.VisualStudio.Package.LanguageService> classe charge un ensemble par défaut d’icônes. Dans la mesure où vous spécifiez l’index d’image exactement là où vous avez besoin d’icônes, comment vous organisez votre propre liste d’images est dépend entièrement de vous.  
  
### <a name="images-used-in-intellisense-completion-lists"></a>Images utilisées dans les listes de saisie semi-automatique IntelliSense  
 Pour les listes de saisie semi-automatique IntelliSense, l’index d’image est spécifié pour chaque élément dans le <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> méthode de la <xref:Microsoft.VisualStudio.Package.Declarations> (classe), que vous devez remplacer si vous souhaitez fournir un index d’image. La valeur retournée par la <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> méthode est un index dans la liste d’images fournie à la <xref:Microsoft.VisualStudio.Package.CompletionSet> constructeur de classe qui est la même liste d’images est retournée par la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe (vous pouvez modifier la liste à laquelle image utiliser pour le <xref:Microsoft.VisualStudio.Package.CompletionSet> si vous remplacez le <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.Source> classe pour fournir une liste d’images différents).  
  
### <a name="images-used-in-the-navigation-bar"></a>Images utilisées dans la barre de Navigation  
 Le **barre de Navigation** affiche les listes des types et membres et est utilisé pour la navigation rapide peut afficher des icônes. Ces icônes sont obtenues à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.LanguageService> classe et ne peut pas être remplacée spécifiquement pour le **barre de Navigation**. Les index utilisés pour chaque élément dans les zones de liste déroulante sont spécifiés lorsque les listes représentant des zones de liste déroulante sont remplies le <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe (voir [prise en charge de la barre de Navigation dans un Service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Ces index d’image est d’une certaine manière obtenues à partir de l’analyseur, généralement par le biais de votre version de la <xref:Microsoft.VisualStudio.Package.Declarations> classe. Comment les index sont obtenus dépend entièrement de vous.  
  
### <a name="images-used-in-the-error-list-task-window"></a>Images utilisées dans la tâche de fenêtre de la liste d’erreurs  
 Chaque fois que le <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Analyseur de méthode (voir [Analyseur de Service de langage hérité et le moteur d’analyse](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) rencontre une erreur et transmet cette erreur pour le <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> méthode dans le <xref:Microsoft.VisualStudio.Package.AuthoringSink> (classe), l’erreur est signalée dans le  **Liste d’erreurs** fenêtre des tâches. Une icône peut être associée à chaque élément qui apparaît dans la fenêtre des tâches et que cette icône proviennent de la même liste d’images retournée à partir de la <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> méthode dans la <xref:Microsoft.VisualStudio.Package.LanguageService> classe. Le comportement par défaut des classes MPF est de ne pas afficher une image avec le message d’erreur. Toutefois, vous pouvez substituer ce comportement en dérivant une classe à partir de la <xref:Microsoft.VisualStudio.Package.Source> classe et en remplaçant le <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> (méthode). Dans cette méthode, vous créez un <xref:Microsoft.VisualStudio.Package.DocumentTask> objet. Avant de retourner cet objet, vous pouvez utiliser la <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> propriété sur le <xref:Microsoft.VisualStudio.Package.DocumentTask> objet à définir l’index d’image. Cela se présente comme dans l’exemple suivant. Notez que `TestIconImageIndex` est une énumération qui répertorie toutes les icônes et est spécifique à cet exemple. Vous pouvez avoir une autre manière d’identifier les icônes dans votre service de langage.  
  
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
            TastPriority      priority,  
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
  
## <a name="the-default-image-list-for-a-language-service"></a>La liste d’images par défaut pour un Service de langage  
 La liste d’images par défaut fournie avec les classes de service de langage MPF base contient un nombre d’icônes associés aux éléments de langage plus courants. La majeure partie de ces icônes sont organisées en ensembles de six variantes, correspondant aux concepts d’accès de public, interne, friend, protected, private et de raccourci. Par exemple, vous pouvez avoir des icônes différentes pour une méthode selon qu’il est public, protégé ou privé.  
  
 L’énumération suivante spécifie les noms par défaut pour chaque jeu d’icônes et spécifie l’index associé. Par exemple, en fonction de l’énumération, vous pouvez spécifier l’index d’image pour une méthode protégée en tant que `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Vous pouvez modifier les noms dans cette énumération comme vous le souhaitez.  
  
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
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Vue d’ensemble du Service de langage hérité](../../extensibility/internals/legacy-language-service-overview.md)   
 [L’inscription d’un Service de langage hérité](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Scanneur et analyseur du service de langage hérité](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

