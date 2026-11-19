# Kairos en Claude

Kairos, el sistema de gestión de seguridad y salud en el trabajo de su empresa, dentro de Claude. Claude entra con
su cuenta de Kairos y tiene sus mismos permisos: consulta, prepara documentos y planes, y hace en Kairos lo que
usted le pida. Lo legal (firmar, calificar, confirmar) se lo pregunta antes, y la salud de cada persona solo se ve
en Kairos.

## Instalar

**Claude Code**

```
/plugin marketplace add matrujillo10/kairos-claude
/plugin install kairos@kairos
```

La primera vez que Claude use Kairos, se abre Kairos para que usted entre y autorice.

**Cowork, para toda su organización**

Quien administra la organización en claude.ai agrega este plugin desde su repositorio de plugins (Organization
settings › Plugins & skills), con esta fuente:

```json
{ "name": "kairos", "source": { "source": "git-subdir", "url": "matrujillo10/kairos-claude", "path": "plugins/kairos" } }
```

**claude.ai**

En Configuración › Conectores, agregue un conector personalizado con la dirección
`https://api.v2.kairos.sg-sst.io/mcp`.

Este repositorio es una copia de solo lectura: los cambios se hacen en Kairos.
