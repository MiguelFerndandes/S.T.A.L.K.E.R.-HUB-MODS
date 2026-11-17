# S.T.A.L.K.E.R. HUB — catálogo de mods

Repositório público do catálogo online do S.T.A.L.K.E.R. HUB para Call of
Pripyat. Os pacotes são distribuídos como assets de GitHub Releases; este
repositório contém somente o manifesto e as instruções de publicação.

## Publicar um mod

1. Publique um ZIP em uma Release deste repositório.
2. O ZIP deve conter apenas a pasta `gamedata` e seus arquivos, sem uma pasta
   externa envolvendo-a. Não inclua executáveis ou conteúdo sem autorização.
3. Calcule o SHA-256 do ZIP, por exemplo no PowerShell:

   ```powershell
   Get-FileHash .\meu-mod.zip -Algorithm SHA256
   ```

4. Adicione uma entrada ao `mods.json` com a tag da Release, o nome exato do
   asset e o hash retornado:

   ```json
   {
     "version": 1,
     "mods": [
       {
         "id": "meu-mod",
         "name": "Meu mod",
         "version": "1.0.0",
         "description": "Descrição curta do mod.",
         "releaseTag": "meu-mod-v1.0.0",
         "asset": "meu-mod.zip",
         "sha256": "SHA256_DE_64_CARACTERES"
       }
     ]
   }
   ```

O HUB valida o manifesto e o hash do ZIP antes de instalar. São aceitos somente
arquivos dentro de `gamedata`; caminhos inválidos, links e conteúdo fora dessa
pasta são rejeitados. Não há mods de terceiros incluídos neste repositório.
