## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>Initialiser les ressources de débogage avec l’extension VS Code
Tout d’abord, nous devons configurer notre projet de code de sorte que VS Code communique avec notre environnement de développement dans Azure. L’extension VS Code pour Connected Environment fournit une commande d’assistance pour configurer le débogage. 

Ouvrez la **palette de commandes** (via le menu **Affichage | Palette de commandes**) et utilisez la saisie semi-automatique pour taper et sélectionner cette commande : `Connected Environment: Create configuration files for connected development`. 

La configuration du débogage pour Connected Environment est alors ajoutée sous le dossier `.vscode`.

![](../media/vsce-command-palette.png)

> [!Note]
> **IMPORTANT** : En raison d’un bogue, fermez et rouvrez VS Code avant de continuer.