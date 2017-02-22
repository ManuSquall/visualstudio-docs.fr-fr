---
title: "L’impl&#233;mentation d’un Service2 de langage h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services de langage (framework package managé), l’implémentation"
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Impl&#233;mentation d’un Service de langage h&#233;rit&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Pour implémenter un service de langage à l'aide de managed package \(MPF\), vous devez dériver une classe de la classe d' <xref:Microsoft.VisualStudio.Package.LanguageService> et implémenter les méthodes et les propriétés abstraites suivantes :  
  
-   Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>  
  
-   Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
-   Méthode <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>  
  
-   La propriété <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>  
  
 Consultez les sections pertinentes ci\-dessous pour plus d'informations sur l'implémentation de ces méthodes et propriétés.  
  
 Pour prendre en charge des fonctionnalités supplémentaires, votre service de langage peut dériver une classe d'une classe de service de langage de MPF ; par exemple, pour prendre en charge les commandes de menu supplémentaires, vous devez dériver une classe de la classe d' <xref:Microsoft.VisualStudio.Package.ViewFilter> et substituer plusieurs des méthodes de gestion de commande \(voir l' <xref:Microsoft.VisualStudio.Package.ViewFilter> pour plus d'informations\).  La classe d' <xref:Microsoft.VisualStudio.Package.LanguageService> fournit un certain nombre de méthodes qui sont appelées pour créer de nouvelles instances de classes différentes et vous substituez la méthode appropriée de design pour fournir une instance de votre classe.  Par exemple, vous devez substituer la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> dans la classe d' <xref:Microsoft.VisualStudio.Package.LanguageService> pour retourner une instance de votre propre classe d' <xref:Microsoft.VisualStudio.Package.ViewFilter> .  Consultez la section « en instanciant classes personnalisées » pour plus de détails.  
  
 Votre service de langage peut également fournir ses propres icônes, utilisées dans plusieurs.  Par exemple, lorsqu'une liste de saisie semi\-automatique Intellisense est affichée, chaque élément de la liste peut avoir une icône qui lui est associée, marquant l'élément en tant que méthode, classe, l'espace de noms, propriété, ou celui qui est nécessaire pour votre langage.  ces icônes sont utilisées dans toutes les listes d'Intellisense, **barre de navigation**, et dans la fenêtre de tâche de **Liste d'erreurs** .  Consultez la section « d'images de service de langage » ci\-dessous pour plus de détails.  
  
## méthode de GetLanguagePreferences  
 La méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> retourne toujours la même instance d'une classe d' <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  Vous pouvez utiliser la classe de base d' <xref:Microsoft.VisualStudio.Package.LanguagePreferences> si vous n'avez besoin d'aucune préférence supplémentaires pour votre service de langage.  Les classes de service de langage de MPF s'appuient sur la présence au moins de la classe de base d' <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  
  
### Exemple  
 Cet exemple montre une implémentation de la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> .  cet exemple utilise la classe de base d' <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .  
  
```c#  
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
  
## méthode de GetScanner  
 Cette méthode retourne une instance d'un objet d' <xref:Microsoft.VisualStudio.Package.IScanner> qui implémente un analyseur ou un scanner au niveau de la ligne utilisé pour obtenir des jetons et leurs types et déclencheurs.  Ce scanner est utilisé dans la classe d' <xref:Microsoft.VisualStudio.Package.Colorizer> pour la colorisation bien que le scanner puisse également être utilisé pour obtenir des types de jetons et des déclencheurs comme prélude à une opération d'analyse plus complexe.  Vous devez fournir la classe qui implémente l'interface d' <xref:Microsoft.VisualStudio.Package.IScanner> et vous devez implémenter toutes les méthodes sur l'interface d' <xref:Microsoft.VisualStudio.Package.IScanner> .  
  
### Exemple  
 Cet exemple montre une implémentation de la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> .  La classe d' `TestScanner` implémente l'interface d' <xref:Microsoft.VisualStudio.Package.IScanner> \(non affichée\).  
  
```c#  
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
  
## méthode de ParseSource  
 Analyse le fichier source sur un certain nombre de différentes raisons.  Cette méthode reçoit un objet d' <xref:Microsoft.VisualStudio.Package.ParseRequest> qui décrit ce qui est attendu d'une opération d'analyse particulière.  La méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> appelle un analyseur plus complexe qui détermine la fonctionnalité et la portée de jeton.  La méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> est utilisée une prise aux opérations Intellisense ainsi que les accolades correspondantes.  Même si vous ne prennent pas en charge de telles opérations avancées, vous devez toujours retourner un objet valide d' <xref:Microsoft.VisualStudio.Package.AuthoringScope> et que vous obligent à créer une classe qui implémente l'interface d' <xref:Microsoft.VisualStudio.Package.AuthoringScope> et implémente toutes les méthodes sur cette interface.  Vous pouvez retourner des valeurs NULL dans toutes les méthodes mais l'objet d' <xref:Microsoft.VisualStudio.Package.AuthoringScope> ne doit pas être une valeur NULL.  
  
### Exemple  
 Cet exemple montre une implémentation minimale de la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> et de la classe d' <xref:Microsoft.VisualStudio.Package.AuthoringScope> , suffisant pour permettre au service de langage pour compiler et exécuter sans l'un des réellement de prise en charge des fonctionnalités avancées.  
  
```c#  
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
  
## propriété Name  
 Cette propriété retourne le nom du service de langage.  Cela doit être le même nom donné lorsque le service de langage a été enregistré.  Ce nom est utilisé dans un certain nombre de bits, le plus important qui est la classe d' <xref:Microsoft.VisualStudio.Package.LanguagePreferences> dont le nom est utilisé pour accéder au Registre.  Le nom retourné par cette propriété ne doit pas être localisé lorsqu'il est utilisé dans le Registre pour l'entrée du Registre et les noms de clés.  
  
### Exemple  
 cet exemple montre une implémentation possible de la propriété d' <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> .  Notez que le nom ici est codé en dur : le nom réel doit être obtenu à partir d'un fichier de ressources afin qu'il puisse être utilisé en enregistrant un service de langage \(consultez [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md)\).  
  
```c#  
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
  
## instancier les classes personnalisées  
 les méthodes suivantes dans les classes spécifiées peuvent être substituées pour fournir des instances de vos propres versions de chaque classe.  
  
### dans la classe de LanguageService  
  
|Méthode|classe retournée|Description|  
|-------------|----------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|pour prendre en charge les ajouts personnalisés à l'affichage de texte.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Pour prendre en charge des propriétés de document personnalisées.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|pour prendre en charge **barre de navigation**.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Pour prendre en charge des fonctions dans les modèles d'extrait de code.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Pour prendre en charge des extraits de code \(cette méthode n'est pas généralement substituée\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Pour prendre en charge la personnalisation de la structure d' <xref:Microsoft.VisualStudio.Package.ParseRequest> \(cette méthode n'est pas généralement substituée\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Pour prendre en charge le code source de mise en forme, en spécifiant des caractères de commentaire, et personnalisation des signatures de méthode.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Pour prendre en charge les commandes de menu supplémentaires.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Pour prendre en charge la mise en surbrillance de la syntaxe \(cette méthode n'est pas généralement substituée\).|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|pour prendre en charge l'accès aux langues.  Cette méthode doit être implémentée mais peut retourner une instance de la classe de base.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|pour fournir un analyseur utilisé pour identifier des types de jetons sur une ligne.  cette méthode doit être implémentée et <xref:Microsoft.VisualStudio.Package.IScanner> doit être dérivé de.|  
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Pour fournir un analyseur utilisé pour identifier la fonctionnalité et la portée dans un fichier source entier.  Cette méthode doit être implémentée et doit retourner une instance de votre version de la classe d' <xref:Microsoft.VisualStudio.Package.AuthoringScope> .  Si vous souhaitez prendre en charge est une syntaxe de mise en surbrillance \(qui requiert l'analyseur d' <xref:Microsoft.VisualStudio.Package.IScanner> retourné par la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> \), vous pouvez ne rien dans cette méthode autre que le retour une version des méthodes de la classe d' <xref:Microsoft.VisualStudio.Package.AuthoringScope> laquelle toutes les valeurs NULL de retour.|  
  
### dans la classe de source  
  
|Méthode|classe retournée|Description|  
|-------------|----------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Pour personnaliser l'affichage des listes de saisie semi\-automatique Intellisense \(cette méthode n'est pas généralement substituée\).|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|pour les marques de prise en charge dans la liste des tâches de liste d'erreurs ; spécifiquement, la prise en charge des fonctionnalités au delà d'ouvrir le fichier et d'accéder à la ligne qui a provoqué l'erreur.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Pour personnaliser l'affichage des info\-bulles des informations sur les paramètres Intellisense.|  
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Pour le code commentant de prise en charge.|  
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Pour collecter des informations pendant l'opération d'analyse.|  
  
### dans la classe d'AuthoringScope  
  
|Méthode|classe retournée|Description|  
|-------------|----------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Fournit une liste des déclarations telles que les membres ou types.  Cette méthode doit être implémentée mais peut retourner une valeur NULL.  Si cette méthode retourne un objet valide, l'objet doit être une instance de votre version de la classe d' <xref:Microsoft.VisualStudio.Package.Declarations> .|  
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Fournit une liste des signatures de méthode pour un contexte donné.  Cette méthode doit être implémentée mais peut retourner une valeur NULL.  Si cette méthode retourne un objet valide, l'objet doit être une instance de votre version de la classe d' <xref:Microsoft.VisualStudio.Package.Methods> .|  
  
## Images de service de langage  
 Pour fournir une liste d'icônes à utiliser dans tout le service de langage, substituez la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> dans la classe d' <xref:Microsoft.VisualStudio.Package.LanguageService> et retournez <xref:System.Windows.Forms.ImageList> contenant les icônes.  Les charges d'une classe de base d' <xref:Microsoft.VisualStudio.Package.LanguageService> un ensemble par défaut des icônes.  Étant donné que vous spécifiez l'index exact d'image dans ces emplacements qui ont besoin d'icônes, comment vous réorganisez le votre propre liste d'images dépend entièrement à vous.  
  
### Images utilisées dans les listes de saisie semi\-automatique Intellisense  
 Pour les listes de saisie semi\-automatique Intellisense, l'index d'image est spécifié pour chaque élément de la méthode d' <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> de classe d' <xref:Microsoft.VisualStudio.Package.Declarations> , que vous devez substituer si vous souhaitez fournir un index d'image.  La valeur retournée par la méthode d' <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> est un index dans la liste d'images fournie au constructeur de classe d' <xref:Microsoft.VisualStudio.Package.CompletionSet> et il est identique à la liste d'images retournée par la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> dans la classe d' <xref:Microsoft.VisualStudio.Package.LanguageService> \(vous pouvez changer qui liste d'images à utiliser pour <xref:Microsoft.VisualStudio.Package.CompletionSet> si vous substituez la méthode d' <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> dans la classe d' <xref:Microsoft.VisualStudio.Package.Source> pour fournir une liste d'images différente\).  
  
### images utilisées dans la barre de navigation  
 **barre de navigation** affiche les listes de types et de membres et est utilisé pour la navigation rapide peut afficher des icônes.  ces icônes sont obtenues à partir de la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> dans la classe d' <xref:Microsoft.VisualStudio.Package.LanguageService> et ne peuvent pas être substituées spécifiquement pour **barre de navigation**.  Les index utilisés pour chaque élément dans les zones de liste déroulante sont spécifiés lorsque les listes représentant les zones de liste déroulante sont effectuées la méthode d' <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> dans la classe d' <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> \(consultez [Prise en charge de la barre de Navigation dans un Service de langage hérité](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)\).  Ces index d'image sont obtenus d'une certaine manière à partir de l'analyseur, généralement via votre version de la classe d' <xref:Microsoft.VisualStudio.Package.Declarations> .  Comment les index sont obtenus dépend entièrement à vous.  
  
### images utilisées dans la fenêtre de tâche de liste d'erreurs  
 Chaque fois que l'analyseur de méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(consultez [Scanneur et analyseur du Service de langage ancien](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)\) rencontre une erreur et les séries que l'erreur à la méthode d' <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> dans la classe d' <xref:Microsoft.VisualStudio.Package.AuthoringSink> , l'erreur est stocké dans la fenêtre de tâche de **Liste d'erreurs** .  Une icône peut être associée à chaque élément figurant dans la fenêtre de tâche et l'icône provient de la même liste d'images retournée par la méthode d' <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> dans la classe d' <xref:Microsoft.VisualStudio.Package.LanguageService> .  Le comportement par défaut des classes de MPF consiste à ne pas afficher une image avec le message d'erreur.  Toutefois, vous pouvez substituer ce comportement en dérivant une classe de la classe d' <xref:Microsoft.VisualStudio.Package.Source> et en substituant la méthode d' <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> .  dans cette méthode, vous créez un nouvel objet d' <xref:Microsoft.VisualStudio.Package.DocumentTask> .  Avant de retourner cet objet, vous pouvez utiliser la propriété d' <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> sur l'objet d' <xref:Microsoft.VisualStudio.Package.DocumentTask> pour définir l'index d'image.  Cela peut se présenter présenter comme dans l'exemple suivant.  notez qu' `TestIconImageIndex` est une énumération qui répertorie toutes les icônes et est spécifique à cet exemple.  Vous pouvez avoir une autre façon d'identifier des icônes dans votre service de langage.  
  
```c#  
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
  
## La liste d'images par défaut pour un service de langage  
 La liste d'images par défaut fournie avec les classes de service de langage de la base MPF contient un nombre quelconque d'icônes associées aux éléments de langage plus courant.  La partie de ces icônes sont organisées dans les ensembles de six variations, correspondant aux concepts d'accès du publiques, internes, de la fonction friend, protégé, privé, et du raccourci.  Par exemple, vous pouvez avoir des icônes différentes pour un selon que la méthode qu'il est public, protégé ou privé.  
  
 L'énumération suivante spécifie les noms classiques pour chaque jeu d'icônes et spécifie l'index associé.  Par exemple, en fonction de l'énumération, vous pouvez spécifier l'index d'image pour une méthode protégée comme `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`.  Vous pouvez modifier les noms dans cette énumération comme vous le souhaitez.  
  
```c#  
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
  
## Voir aussi  
 [Implémentation d’un Service de langage hérité](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Vue d’ensemble du Service de langage ancien](../../extensibility/internals/legacy-language-service-overview.md)   
 [L’inscription d’un Service de langage](../../extensibility/internals/registering-a-legacy-language-service1.md)   
 [Scanneur et analyseur du Service de langage ancien](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)