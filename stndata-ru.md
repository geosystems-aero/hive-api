# Структура документа json/stndata

```typescript
interface stndata {
  "id": { // ключ - числовой идентификатор станции
    "id": number, // числовой идентификатор станции, напр. 7
    "name": string, // кодовое имя станции, напр. "MINP"
    "lat": number, // широта, градусы, напр. 55.006091097
    "lon": number, // долгота, градусы, напр. 73.343303117
    "hgt": number, // высота, метры, напр. 90.61,
    "ant_hgt": number|null, // (опционально) высота антенны над маркером, метры 
    "igsantenna": string|null, // IGS-код антенны, напр. "TRM39105.00" 
    "igsrcvr": string|null, // IGS-код приёмника, напр. "NOV OEMV3"
    "state": string, /* базовый статус станции 
      "connected" = работает, сейчас в сети; "disconnected" = сейчас не в сети; "disabled" = отключена */ 
    "gnsses": string|null, /* поддерживаемые ГНСС, строка из однобуквенных кодов
      G = GPS, R = GLONASS, E = Galileo, J = QZSS, S = SBAS, C = BDS (BeiDou, Compass) */
    "lastEpoch": number|null, /* Отметка времени последней полученной эпохи, UNIX-время 
      (напр. 1507719612000 = 11.10.2017 11:25:53.000) */
    "lastEpochSys": number|null, /* Системное время последней полученной эпохи, UNIX-время 
      (напр. 1507721135185 = 11.10.2017 11:25:35.185). 
      lastEpochSys = lastEpoch + (задержка от станции до сервера) - секунды координации */ 
    "pastAvail": number, // доступность данных за последние 7 дней (1.0 = 100%)
    "params": {
      "location_country": string|null, // страна, напр. "Российская Федерация"
      "location_region": string|null, // регион и район/населённый пункт, напр. "Омская область, Омск"
      "location_city": string|null, // населённый пункт, напр. "Омск"
      "rcvr_serial": string|null, // серийный номер приёмника, напр. "DAB10090048"
      "antenna_serial": string|null, // серийный номер антенны
      "radome_code": string|null, // IGS-код обтекателя, напр. "TPSH"
      "override_state": string |null/* расширенный статус станции
        "temporary" = временная, "experimental" = экспериментальная, "decommissioned" = демонтирована,
        "maintenance" = на тех. обслуживании */
    }
  }
}
```