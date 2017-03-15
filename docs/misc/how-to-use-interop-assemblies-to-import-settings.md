---
title: "Proc&#233;dure&#160;: utilisation des assemblys PIA pour importer des param&#232;tres | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paramètres IDE, importation à l’aide des assemblys PIA"
  - "IDE, importation des paramètres à l’aide des assemblys PIA"
  - "paramètres utilisateur [SDK Visual Studio], importation à l’aide des assemblys PIA"
ms.assetid: 8a43dbe2-fdc0-471b-8235-3f489b77db0f
caps.latest.revision: 26
caps.handback.revision: 26
manager: "douge"
---
# Proc&#233;dure&#160;: utilisation des assemblys PIA pour importer des param&#232;tres
Un VSPackage peut importer des paramètres à partir de l’environnement de développement intégré \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. L’IDE utilise l’implémentation de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> d’un VSPackage pour déterminer comment récupérer la configuration du VSPackage.  
  
> [!NOTE]
>  L’infrastructure MPF \(Managed Package Framework\) fournit un ensemble de classes managées pour faciliter la création d’extensions Visual Studio. Pour effectuer cette tâche à l’aide de MPF, consultez [Importation des paramètres](/visual-cpp/misc/importing-settings).  
  
### Pour implémenter l’importation des paramètres dans un VSPackage  
  
1.  Implémentez la prise en charge de base du mécanisme de paramètres [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
    -   Inscrivez le VSPackage comme prenant en charge le mécanisme de paramètres en définissant un ou plusieurs Points de paramètres personnalisés.  
  
         Pour plus d’informations, consultez [Prise en charge pour les paramètres utilisateur](../extensibility/internals/support-for-user-settings.md).  
  
    -   Déclarez que le VSPackage implémente l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings>, par exemple :  
  
        ```  
        public class MyPackage : IVsPackage, IVsUserSettings, IVsUserSettingsQuery  
        ```  
  
    -   Vérifiez que l’implémentation de la méthode <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A> du VSPackage fournit une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> lorsqu’elle est appelée avec `IID_IVsUserSettings`. Exemple :  
  
        ```  
        STDMETHODIMP MyPackage::QueryInterface(THIS_ REFIID riid, LPVOID FAR* ppvObj) { if (ppvObj == NULL) return E_POINTER; *ppvObj = NULL; if (riid == IID_IUnknown) *ppvObj = (LPVOID)(IUnknown *)(IClassFactory*)this; else if (riid == IID_IClassFactory) *ppvObj = (LPVOID)(IClassFactory *)this; else if (riid == IID_IVsPackage) *ppvObj = (LPVOID)(IVsPackage *)this; else if (riid == IID_IVsPersistSolutionOpts) *ppvObj = (LPVOID)(IVsPersistSolutionOpts *)this; else if (riid == IID_IVsPersistSolutionProps) *ppvObj = (LPVOID)(IVsPersistSolutionProps *)this; else if (riid == IID_IVsComponentSelectorProvider) *ppvObj = (LPVOID)(IVsComponentSelectorProvider *)this; else if (riid == IID_IVsUserSettings) *ppvObj = (LPVOID)(IVsUserSettings *)this; else if (riid == IID_IVsUserSettingsQuery) *ppvObj = (LPVOID)(IVsUserSettingsQuery *)this; if (*ppvObj) { AddRef(); return NOERROR; } return E_NOINTERFACE; }  
        ```  
  
2.  Récupérez les informations de paramètres.  
  
     Pour prendre en charge la récupération des informations de paramètres, un VSPackage doit implémenter la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A>.  
  
     Pour lire des données, l’implémentation de l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings> d’un VSPackage doit utiliser les deux premiers arguments transmis par l’IDE : le GUID de la catégorie de ce Point de paramètres personnalisés et une interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader>.  
  
    1.  L’implémentation de la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> d’un VSPackage doit vérifier le GUID de catégorie transmis et choisir le mécanisme approprié pour l’état de récupération.  
  
         Dans l’exemple ci\-dessous, la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> appelle une implémentation différente pour récupérer l’état de la barre de commandes plutôt que l’état des liaisons de clés.  
  
    2.  Un VSPackage doit utiliser l’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> fournie pour récupérer les données dans le fichier de paramètres.  
  
        > [!NOTE]
        >  Si les informations de paramètres varient en fonction de la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], l’implémentation de la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> d’un VSPackage doit utiliser la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> avant de lire les données pour vérifier la version de l’IDE.  
  
         L’interface fournit des méthodes pour lire différents types de données dans le fichier de paramètres.  
  
         `interface IVsSettingsReader : IUnknown`  
  
         `{`  
  
         `HRESULT ReadSettingString(WCHAR *pszSettingName, BSTR *pbstrSettingValue);`  
  
         `HRESULT ReadSettingLong(WCHAR *pszSettingName, long *plSettingValue);`  
  
         `HRESULT ReadSettingBoolean(WCHAR *pszSettingName, BOOL *pfSettingValue);`  
  
         `HRESULT ReadSettingAttribute(LPCOLESTR pszSettingName,LPCOLESTR pszAttributeName, BSTR *pbstrSettingValue);  //Internal use only`  
  
         `HRESULT ReadSettingBytes(WCHAR *pszSettingName, BYTE *pSettingValue, long *plDataLength, long lDataMax);`  
  
         `HRESULT ReadVersion(int *pnMajor, int *pnMinor, int *pnBuild);`  
  
         `HRESULT ReportError(WCHAR *pszError);`  
  
         `};`  
  
     Le fichier de paramètres prend en charge l’accès aléatoire aux données. Ainsi, l’ordre des opérations de lecture et d’écriture de paramètres n’est pas important.  
  
     Ceci est illustré par l’état de barre de commandes d’exportation et d’importation \(`ExportSettings_CommandBa`r et `ImportSettings_CommandBar`\) de l’implémentation dans l’exemple ci\-dessous.  
  
3.  Validez les données récupérées.  
  
     Les informations de paramètres sont contenues dans des fichiers XML qui peuvent être modifiés manuellement.  
  
> [!IMPORTANT]
>  Les informations de paramètres peuvent être endommagées sur le disque, peuvent contenir des paramètres propres à la version et peuvent être utilisées comme véhicule pour des attaques malveillantes. La validité de chaque élément de données retourné par la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader> doit être confirmée.  
  
-   Pour vérifier la prise en charge de la version de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilisée pour générer les paramètres récupérés, appelez la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReadFileVersion%2A> pour récupérer la version.  
  
-   Pour que l’IDE signale à l’utilisateur qu’un élément de données importé n’est pas validé, un VSPackage appelle la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsReader.ReportError%2A>.  
  
1.  Appliquez les informations de paramètres.  
  
    1.  L’implémentation de la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> doit respecter la valeur du troisième argument que l’IDE lui a passé. Les valeurs prises en charge sont des membres de l’énumération <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>. Pour plus d’informations, consultez <xref:Microsoft.VisualStudio.Shell.Interop.__UserSettingsFlags>.  
  
         Dans l’exemple ci\-dessous, l’implémentation pour l’importation des paramètres de barre de commandes \(`ImportSettings_Commandbar`\) utilise la valeur de cet argument pour déterminer s’il faut appliquer des paramètres pour remplacer les valeurs existantes ou pour les mettre à jour de manière additive.  
  
    2.  Vous devez implémenter une méthodologie de cache à double écriture lors de l’application de paramètres importés.  
  
         Les informations d’état dans le Registre ou le système de fichiers doivent être mises à jour en même temps que les paramètres sont appliqués à l’IDE. Cela garantit la cohérence de la configuration et la prise en charge des scénarios d’IDE à instances multiples.  
  
2.  Indiquez à l’IDE comment gérer l’importation des paramètres.  
  
     Utilisez l’argument `pfRestartRequired` retourné par la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> pour signaler à l’IDE si un redémarrage est nécessaire pour appliquer les paramètres importés.  
  
     Si l’implémentation de la méthode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ImportSettings%2A> du VSPackage retourne `true`, l’utilisateur est invité à redémarrer l’IDE.  
  
## Exemple  
 L’exemple suivant montre comment importer et exporter des données de paramètres.  
  
```  
static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // -------------------------------------------------------------------------- //    IVsUserSettings methods used for configuration export and import //    Delegate to the right shell object based on the category GUID // -------------------------------------------------------------------------- static const WCHAR c_szFirstSettingName[] = L"FirstSettingName"; static const WCHAR c_szRandomTrashBytes[] = L"RandomTrashBytes"; static const WCHAR c_szRandomTrashLength[] = L"RandomTrashLength"; static const WCHAR c_szBreakPointWindow[] = L"Breakpoints Window"; // Export Settings. STDMETHOD(NeedExport)(WCHAR* pszCategoryGUID, BOOL *pfNeedExport) { if (!pfNeedExport) return E_INVALIDARG; CLSID clsidCategory; HRESULT hr= S_OK; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); if (GUID_Profiles_CommandBars == clsidCategory) { *pfNeedExport = TRUE; //Always export Command Bar Configuration }else if (GUID_Profiles_KeyBindings == clsidCategory) { *pfNeedExport = FALSE; //By Default don't export key bindings if (m_fMake_Permanent) *pfNeedExport = TRUE; //Export if user wants current configuration saved. }else{ hr = E_UNEXPECTED; } Error: return hr; } STDMETHOD(ExportSettings)(WCHAR *pszCategoryGUID, IVsSettingsWriter *pSettings) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ExportSettings_CommandBars(pSettings); }else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ExportSettings_KeyBindings(pSettings); }else{ hr = E_UNEXPECTED; } Error: return hr; }; HRESULT ExportSettings_CommandBars(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szFirstSettingName, L"Value1"); IfFailGo(hr); int cRandomTrash = 12345; BYTE *pRandomTrash = (BYTE *)VSAlloc(cRandomTrash); if (pRandomTrash){ hr = pSettings->WriteSettingBytes(c_szRandomTrashBytes, pRandomTrash, cRandomTrash); IfFailGo(hr); hr = pSettings->WriteSettingLong(c_szRandomTrashLength, cRandomTrash); IfFailGo(hr); } Error: return hr; }; HRESULT ExportSettings_KeyBindings(IVsSettingsWriter *pSettings) { if (!pSettings) return E_INVALIDARG; hr = pSettings->WriteSettingString(c_szBreakPointWindow, L"Ctrl + Alt + B"); IfFailGo(hr); Error: return hr; }; STDMETHOD(ImportSettings)(WCHAR *pszCategoryGUID, IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { CLSID clsidCategory; HRESULT hr; hr = CLSIDFromString(pszCategoryGUID, &clsidCategory); IfFailGo(hr); // Delegate to the right internal implementation based on the requested category. if (GUID_Profiles_CommandBars == clsidCategory) { hr = ImportSettings_CommandBars(, pSettings, flags, pfRestartRequired); } else if (GUID_Profiles_KeyBindings == clsidCategory) { hr = ImportSettings_KeyBindings( pSettings, flags, pfRestartRequired); } else { hr = E_UNEXPECTED; } Error: return hr; }; // Import Settings. HRESULT ImportSettings_CommandBars(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrFirstSettingName; long lTrashLength = 0; BYTE *pTrashBytes = NULL; // Determines whether to import as an additive operation, or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szFirstSettingName, &bstrFirstSettingName); IfFailGo(hr); hr = pSettings->ReadSettingLong(c_szRandomTrashLength, &lTrashLength); IfFailGo(hr); if (lTrashLength > 0) { pTrashBytes = (BYTE*)VSAlloc(lTrashLength); IfNullMemGo(pTrashBytes); long lDataRead = 0; hr = pSettings->ReadSettingBytes(c_szRandomTrashLength, pTrashBytes, &lDataRead, lTrashLength); IfFailGo(hr); if (lDataRead != lTrashLength) { hr = E_UNEXPECTED; goto Error; } } // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_CommandBar(bstrFirstSettingName,lTrashLength,pTrashBytes,lDataRead); Error: return hr; }; HRESULT ImportSettings_KeyBindings(IVsSettingsReader *pSettings, UserSettingsFlags flags, BOOL *pfRestartRequired) { if (!pSettings) return E_INVALIDARG; if (pfRestartRequired) { *pfRestartRequired = FALSE; //Nobody should require a restart!! } CComBSTR bstrBreakPointWindow; // Determines whether to import as an additive operation or a reset all settings operation. BOOL fResetCompletely = FALSE; if (flags & USF_ResetOnImport) fResetCompletely = TRUE; hr = pSettings->ReadSettingString(c_szBreakPointWindow, &bstrBreakPointWindow); IfFailGo(hr); // Note: before returning these settings should immediately be applied to your personal //            settings store, whether in the registry or the file system. // This write-thru cache methodology is essential to work in multi-instance IDE scenarios. hr = UpdateState_KeyBindings(bstrBreakPointWindow); Error: return hr; }  
```  
  
## Voir aussi  
 [Procédure : exportation de paramètres à l’aide des assemblys d’interopérabilité](../misc/how-to-export-settings-by-using-interop-assemblies.md)   
 [Prise en charge pour les paramètres utilisateur](../extensibility/internals/support-for-user-settings.md)   
 [Options et paramètres d'extension utilisateur](../extensibility/extending-user-settings-and-options.md)   
 [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3)