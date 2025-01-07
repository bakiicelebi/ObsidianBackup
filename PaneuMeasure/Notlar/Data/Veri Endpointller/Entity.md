@Id  
@Column(name = "MEASURE_ID", nullable = false)  
private Long measureId;  
  
@Column(name = "CHECK_ITEM_ID",nullable = false)  
private Long checkItemId;  
  
@ManyToOne(fetch = FetchType._LAZY_)  
@JoinColumn(name = "CHECK_ITEM_ID", referencedColumnName = "CHECK_ITEM_ID", nullable = false, insertable = false, updatable = false)  
private TmCheckItem checkItem;  
  
@Column(name = "CYCLE",nullable = false)  
private Integer cycle;  
  
@Column(name = "VEHICLE_ID")  
private Long vehicleId;  
  
@Column(name = "PART_NUMBER",length = 64)  
private String partNumber;  
  
@Column(name = "GROUP_ID")  
private Long groupId;  
  
@ManyToOne(fetch = FetchType._LAZY_)  
@JoinColumn(name = "GROUP_ID", referencedColumnName = "GROUP_ID", nullable = false, insertable = false, updatable = false)  
private TmCheckItemGroup checkItemGroup;  
  
@Column(name = "SHIFT_ID")  
private Long shiftId;  
  
@Column(name = "PRODUCTION_DATE")  
private LocalDate productionDate;  
  
@Column(name = "MEASURE_STATUS")  
@Convert(converter = CheckItemMeasureStatus.CheckItemMeasureStatusConverter.class)  
private CheckItemMeasureStatus measureStatus;  
  
@Column(name = "MEASUREMENTS", length = 1024)  
private String measurements;