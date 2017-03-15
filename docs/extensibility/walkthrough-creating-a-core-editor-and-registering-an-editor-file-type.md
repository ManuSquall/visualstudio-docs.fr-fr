---
title: "Création d’un éditeur de base et l’inscription d’un Type de fichier éditeur | Documents Microsoft »"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 7bde276b0d53793f57266c13c5ccf63583f7aacf
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Procédure pas à pas : Création d’un éditeur de base et l’inscription d’un Type de fichier de l’éditeur
Cette procédure pas à pas montre comment créer un VSPackage qui démarre la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal lorsqu’un fichier ayant l’extension de nom de fichier .myext est chargé.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Emplacements pour le modèle de projet de Package Visual Studio  
 Le modèle de projet de package Visual Studio se trouve à trois emplacements différents dans la boîte de dialogue **Nouveau projet** :  
  
1.  Sous l’extensibilité Visual Basic. Le langage par défaut du projet est Visual Basic.  
  
2.  Sous l’extensibilité C#. Le langage par défaut du projet est C#.  
  
3.  Sous l’extensibilité Autres types de projets. Le langage par défaut du projet est C++.  
  
### <a name="to-create-the-vspackage"></a>Pour créer le VSPackage  
  
-   Démarrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et créer un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage intitulé `MyPackage`, comme indiqué dans [procédure pas à pas : création d’un VSPackage de commande de Menu](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Pour ajouter la fabrique d’éditeur  
  
1.  Avec le bouton droit le **MyPackage** du projet, pointez sur **ajouter** , puis **classe**.  
  
2.  Dans le **ajouter un nouvel élément** boîte de dialogue, vérifiez que le **classe** modèle est sélectionné, type `EditorFactory.cs` pour le nom, puis cliquez sur **Add** pour ajouter la classe à votre projet.  
  
     Le fichier EditorFactory.cs doit être ouvert automatiquement.  
  
3.  Référencer les assemblys suivants à partir de votre code.  
  
    ```vb#  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```c#  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  Ajouter un GUID pour le `EditorFactory` classe en ajoutant le `Guid` attribut immédiatement avant la déclaration de classe.  
  
     Vous pouvez générer un nouveau GUID à l’aide du programme guidgen.exe à la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] commande invite ou en cliquant sur **créer un GUID** sur la **outils** menu. Le GUID utilisé ici n'est qu’un exemple ; n’utilisez pas dans votre projet.  
  
    ```vb#  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```c#  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  Dans la définition de classe, ajoutez deux variables privées pour contenir le package parent et un fournisseur de services.  
  
    ```vb#  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```c#  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  Ajoutez un constructeur de classe publique qui prend un paramètre de type <xref:Microsoft.VisualStudio.Shell.Package>:</xref:Microsoft.VisualStudio.Shell.Package>  
  
    ```vb#  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```c#  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  Modifier la `EditorFactory` dériver de déclaration de classe le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
    ```vb#  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```c#  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  Cliquez sur <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, cliquez sur **implémenter l’Interface**, puis cliquez sur **implémenter l’Interface explicitement**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
     Cela ajoute les quatre méthodes qui doivent être implémentées dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interface.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
9. Remplacez le contenu de la méthode `IVsEditorFactory.Close` par le code suivant :  
  
    ```vb#  
    Return VSConstants.S_OK  
    ```  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
10. Remplacez le contenu de la `IVsEditorFactory.SetSite` par le code suivant.  
  
    ```vb#  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```c#  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Remplacez le contenu de la méthode `IVsEditorFactory.MapLogicalView` par le code suivant :  
  
    ```vb#  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```c#  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Remplacez le contenu de la méthode `IVsEditorFactory.CreateEditorInstance` par le code suivant :  
  
    ```vb#  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```c#  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Compilez le projet et n’Assurez-vous qu’aucune erreur.  
  
### <a name="to-register-the-editor-factory"></a>Pour inscrire la fabrique d’éditeur  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur le fichier Resources.resx pour l’ouvrir à la table de chaînes, dans laquelle l’entrée **String1 est** sélectionné.  
  
2.  Modifier le nom de l’identificateur de `IDS_EDITORNAME` et le texte à **MyPackage éditeur.** Cette chaîne s’affiche sous le nom de votre éditeur.  
  
3.  Ouvrez le fichier VSPackage.resx et ajoutez une nouvelle chaîne, le nom de la valeur **101** et la valeur à `IDS_EDITORNAME`. Ainsi, le package avec un ID de ressource pour accéder à la chaîne que vous venez de créer.  
  
    > [!NOTE]
    >  Si le fichier VSPackage.resx contient une autre chaîne que le `name` attribut **101**, remplacer par une autre valeur unique, numérique, ici et dans les étapes suivantes.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le fichier MyPackagePackage.cs.  
  
     Il s’agit du fichier de package principal.  
  
5.  Ajoutez les attributs utilisateur suivant juste avant la `Guid` attribut.  
  
    ```vb#  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```c#  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     Le <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>associe l’extension de fichier .myext à votre fabrique d’éditeur afin que lorsqu’un fichier qui a qu’extension est chargée, votre fabrique d’éditeur est appelée.</xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>  
  
6.  Ajoutez une variable privée pour le `MyPackage` classe, juste avant le constructeur et lui donner le type `EditorFactory`.  
  
    ```vb#  
    Private editorFactory As EditorFactory  
    ```  
  
    ```c#  
    private EditorFactory editorFactory;  
    ```  
  
7.  Rechercher les `Initialize` (méthode) (vous devrez peut-être ouvrir le `Package Members` zone masquée) et ajoutez le code suivant après l’appel à `base.Initialize()`.  
  
    ```vb#  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```c#  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  Compilez le programme et vérifiez l’absence d’erreurs.  
  
     Cette étape enregistre la fabrique d’éditeur dans la ruche expérimentale pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si vous êtes invité à remplacer le fichier resource.h, cliquez sur **OK**.  
  
9. Création d’un fichier nommé TextFile1.myext.  
  
10. Appuyez sur **F5** pour ouvrir une instance de l’instance expérimentale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. Dans l’instance expérimentale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], sur le **fichier** menu, pointez sur **Open** , puis **fichier**.  
  
12. Recherchez TextFile1.myext, puis cliquez sur **ouvrir**.  
  
     Le fichier doit maintenant être chargé.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal gère un large éventail de types de fichier texte et travaille en étroite collaboration avec les services de langage pour fournir un ensemble complet de fonctionnalités telles que la mise en évidence, accolades correspondantes et les listes de saisie semi-automatique par word et membre de saisie semi-automatique IntelliSense. Si vous travaillez avec des fichiers texte, vous pouvez utiliser l’éditeur de base avec un service de langage personnalisé qui prend en charge de vos types de fichiers spécifiques.  
  
 Un VSPackage peut appeler le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur de base en fournissant une fabrique d’éditeur. Cette fabrique d’éditeur est utilisée chaque fois qu’un fichier qui lui est associé est chargé. Si le fichier fait partie d’un projet, l’éditeur principal est automatiquement appelée sauf si votre VSPackage. Toutefois, si le fichier est chargé en dehors d’un projet, puis l’éditeur principal doit être appelé explicitement par votre VSPackage.  
  
 Pour plus d’informations sur l’éditeur principal, consultez [à l’intérieur de l’éditeur de base](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dans l’éditeur de base](../extensibility/inside-the-core-editor.md)   
 [L’instanciation de l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
