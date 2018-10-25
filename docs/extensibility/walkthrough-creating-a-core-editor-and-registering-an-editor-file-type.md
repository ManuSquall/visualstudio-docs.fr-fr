---
title: Création d’un éditeur de base et l’inscription d’un Type de fichier éditeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e00b96d1f5361d3d5260296532be47636f430d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921455"
---
# <a name="walkthrough-create-a-core-editor-and-registering-an-editor-file-type"></a>Procédure pas à pas : Créer un éditeur de base et l’inscription d’un type de fichier d’éditeur
Cette procédure pas à pas montre comment créer un VSPackage qui démarre le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal lorsqu’un fichier avec le *.myext* extension de nom de fichier est chargée.  
  
## <a name="prerequisites"></a>Prérequis  
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Emplacements pour le modèle de projet de Package Visual Studio  
 Le modèle de projet de package Visual Studio se trouve à trois emplacements différents dans la boîte de dialogue **Nouveau projet** :  
  
1.  Sous **Extensibilité Visual Basic**. Le langage par défaut du projet est Visual Basic.  
  
2.  Sous **Extensibilité C#**. Le langage par défaut du projet est C#.  
  
3.  Sous **Extensibilité d’autres types de projets**. Le langage par défaut du projet est C++.  
  
### <a name="to-create-the-vspackage"></a>Pour créer le VSPackage  
  
- Démarrer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et créer un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage nommé `MyPackage`, comme indiqué dans [procédure pas à pas : créer une commande de menu VSPackage](https://msdn.microsoft.com/library/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Pour ajouter la fabrique d’éditeur  
  
1. Cliquez sur le **MyPackage** de projet, pointez sur **ajouter**, puis cliquez sur **classe**.  
  
2. Dans le **ajouter un nouvel élément** boîte de dialogue zone, assurez-vous que le **classe** modèle est sélectionné, type `EditorFactory.cs` pour le nom, puis cliquez sur **ajouter** pour ajouter la classe à votre projet.  
  
    Le *EditorFactory.cs* fichier s’ouvre automatiquement.  
  
3. Référencer les assemblys suivants à partir de votre code.  
  
   ```vb  
   Imports System.Runtime.InteropServices  
   Imports Microsoft.VisualStudio  
   Imports Microsoft.VisualStudio.Shell  
   Imports Microsoft.VisualStudio.Shell.Interop  
   Imports Microsoft.VisualStudio.OLE.Interop  
   Imports Microsoft.VisualStudio.TextManager.Interop  
   Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
   ```  
  
   ```csharp  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio;  
   using Microsoft.VisualStudio.Shell;  
   using Microsoft.VisualStudio.Shell.Interop;  
   using Microsoft.VisualStudio.OLE.Interop;  
   using Microsoft.VisualStudio.TextManager.Interop;  
   using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
   ```  
  
4. Ajouter un GUID vers le `EditorFactory` classe en ajoutant le `Guid` attribut immédiatement avant la déclaration de classe.  
  
    Vous pouvez générer un nouveau GUID à l’aide de la *guidgen.exe* programmation au niveau de la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] invite de commandes, ou en cliquant sur **créer un GUID** sur le **outils** menu. GUID utilisé ici n'est qu’un exemple ; n’utilisez pas dans votre projet.  
  
   ```vb  
   <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
   ```  
  
   ```csharp  
   [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
   ```  
  
5. Dans la définition de classe, ajoutez deux variables privées pour contenir le package parent et un fournisseur de services.  
  
   ```vb  
   Class EditorFactory  
       Private parentPackage As Package  
       Private serviceProvider As IOleServiceProvider  
   ```  
  
   ```csharp  
   class EditorFactory  
   {  
       private Package parentPackage;  
       private IOleServiceProvider serviceProvider;  
   }  
  
   ```  
  
6. Ajoutez un constructeur de classe public qui prend un paramètre de type <xref:Microsoft.VisualStudio.Shell.Package>:  
  
   ```vb  
   Public Sub New(ByVal parentPackage As Package)  
       Me.parentPackage = parentPackage  
   End Sub  
   ```  
  
   ```csharp  
   public EditorFactory(Package parentPackage)  
   {  
       this.parentPackage = parentPackage;  
   }  
   ```  
  
7. Modifier le `EditorFactory` déclaration dériver à partir de classe le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
   ```vb  
   Class EditorFactory Implements IVsEditorFacto  
   ```  
  
   ```csharp  
   class EditorFactory : IVsEditorFactory  
  
   ```  
  
8. Avec le bouton droit <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, cliquez sur **implémenter l’Interface**, puis cliquez sur **implémenter l’Interface explicitement**.  
  
    Cette étape ajoute les quatre méthodes qui doivent être implémentées dans le <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interface.  
  
9. Remplacez le contenu de la méthode `IVsEditorFactory.Close` par le code suivant :  
  
    ```vb  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    return VSConstants.S_OK;  
    ```  
  
10. Remplacez le contenu de la `IVsEditorFactory.SetSite` avec le code suivant.  
  
    ```vb  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```csharp  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Remplacez le contenu de la méthode `IVsEditorFactory.MapLogicalView` par le code suivant :  
  
    ```vb  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```csharp  
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
  
    ```vb  
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
  
    ```csharp  
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
  
13. Compilez le projet et assurez-vous qu’il y a aucune erreur.  
  
### <a name="to-register-the-editor-factory"></a>Pour inscrire la fabrique d’éditeur  
  
1. Dans **l’Explorateur de solutions**, double-cliquez sur le **Resources.resx** fichier ouvrir à la table de chaînes, dans laquelle l’entrée **String1 est** sélectionné.  
  
2. Modifier le nom de l’identificateur à `IDS_EDITORNAME` et le texte à **MyPackage éditeur.** Cette chaîne s’affiche en tant que le nom de votre éditeur.  
  
3. Ouvrez le **VSPackage.resx** de fichiers, ajouter une nouvelle chaîne, la valeur est le nom **101**et définissez la valeur sur `IDS_EDITORNAME`. Cette étape fournit le package avec un ID de ressource pour accéder à la chaîne que vous avez créé.  
  
   > [!NOTE]
   >  Si le **VSPackage.resx** fichier contient une autre chaîne que le `name` attribut la valeur **101**, remplacez par une autre valeur unique, numeric, ici et dans les étapes suivantes.  
  
4. Dans **l’Explorateur de solutions**, ouvrez le **MyPackagePackage.cs** fichier.  
  
    Ce fichier est le fichier de package principal.  
  
5. Ajoutez les attributs d’utilisateur suivant juste avant la `Guid` attribut.  
  
   ```vb  
   <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
   <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
         ".myext", 32, NameResourceID:=101 )> _  
   ```  
  
   ```csharp  
   [ProvideEditorFactory(typeof(EditorFactory), 101)]  
   [ProvideEditorExtension(typeof(EditorFactory),   
         ".myext", 32, NameResourceID = 101)]   
   ```  
  
    Le <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> attribut associe la *.myext* extension à votre fabrique d’éditeur de fichiers afin que chaque fois un fichier qui a qu’extension est chargée, votre fabrique d’éditeur est appelée.  
  
6. Ajouter une variable privée pour le `MyPackage` classe juste avant le constructeur et lui donner le type `EditorFactory`.  
  
   ```vb  
   Private editorFactory As EditorFactory  
   ```  
  
   ```csharp  
   private EditorFactory editorFactory;  
   ```  
  
7. Rechercher la `Initialize` (méthode) (vous devrez peut-être ouvrir le `Package Members` zone masquée) et ajoutez le code suivant après l’appel à `base.Initialize()`.  
  
   ```vb  
   'Create our editor factory and register it.   
   Me.editorFactory = New EditorFactory(Me)  
   MyBase.RegisterEditorFactory(Me.editorFactory)  
   ```  
  
   ```csharp  
   // Create our editor factory and register it.  
   this.editorFactory = new EditorFactory(this);  
   base.RegisterEditorFactory(this.editorFactory);  
  
   ```  
  
8. Compilez le programme et vérifiez l’absence d’erreurs.  
  
    Cette étape inscrit la fabrique d’éditeur dans la ruche expérimentale du Registre pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Si vous êtes invité à remplacer le *resource.h* de fichiers, cliquez sur **OK**.  
  
9. Créer un exemple de fichier nommé *TextFile1.myext*.  
  
10. Appuyez sur **F5** pour ouvrir une instance de l’instance expérimentale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. Dans l’instance expérimentale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dans le **fichier** menu, pointez sur **Open** puis cliquez sur **fichier**.  
  
12. Rechercher **TextFile1.myext** puis cliquez sur **Open**.  
  
     Le fichier doit charger maintenant.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal gère une grande variété de types de fichier texte et fonctionne en étroite collaboration avec les services de langage pour fournir un ensemble complet de fonctionnalités telles que la coloration syntaxique, la correspondance des accolades et la saisie semi-automatique IntelliSense word et les listes de saisie semi-automatique membre. Si vous travaillez avec des fichiers texte, vous pouvez utiliser l’éditeur principal avec un service de langage personnalisé qui prend en charge les types de fichiers spécifiques.  
  
 Un VSPackage peut appeler le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] éditeur principal en fournissant une fabrique d’éditeur. Cette fabrique d’éditeur utilisée chaque fois qu’un fichier qui est associé est chargé. Si le fichier fait partie d’un projet, l’éditeur principal est automatiquement appelée sauf substitution par votre VSPackage. Toutefois, si le fichier est chargé en dehors d’un projet, l’éditeur principal doit être appelé explicitement par votre VSPackage.  
  
 Pour plus d’informations sur l’éditeur principal, consultez [à l’intérieur de l’éditeur principal](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’intérieur de l’éditeur principal](../extensibility/inside-the-core-editor.md)   
 [Instancier l’éditeur principal à l’aide de l’API héritée](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)