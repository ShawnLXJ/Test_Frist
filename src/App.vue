<template>
  <div class="medical-form">
    <!-- 表格标题 -->
    <div class="form-title">四川省院前急救病情记录表（乐山市人民医院）</div>
    <div class="form-subtitle">第一部分：基础信息及初次评估</div>

    <!-- 基本信息部分 -->
    <div class="form-section">
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">姓名：</span>
          <input v-model="formData.name" class="field-value" />
        </div>
        <div class="form-field">
          <span class="field-label">性别：</span>
          <select v-model="formData.gender" class="field-value">
            <option value="">请选择</option>
            <option value="男">男</option>
            <option value="女">女</option>
          </select>
        </div>
        <div class="form-field">
          <span class="field-label">年龄：</span>
          <input v-model="formData.age" class="field-value" type="number" />
        </div>
        <div class="form-field wide-field">
          <span class="field-label">身份证号：</span>
          <input v-model="formData.idNumber" class="field-value" />
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field wide-field">
          <span class="field-label">出警地址：</span>
          <input v-model="formData.dispatchAddress" class="field-value" />
        </div>
        <div class="form-field wide-field">
          <span class="field-label">联系电话：</span>
          <input v-model="formData.contactPhone" class="field-value" />
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">接警时间：</span>
          <input v-model="formData.callTime" class="field-value" type="datetime-local" />
        </div>
        <div class="form-field">
          <span class="field-label">出发时间：</span>
          <input v-model="formData.departureTime" class="field-value" type="datetime-local" />
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">到达现场：</span>
          <input v-model="formData.arrivalTime" class="field-value" type="datetime-local" />
        </div>
        <div class="form-field">
          <span class="field-label">离开时间：</span>
          <input v-model="formData.leaveTime" class="field-value" type="datetime-local" />
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">到达医院：</span>
          <input v-model="formData.hospitalArrivalTime" class="field-value" type="datetime-local" />
        </div>
        <div class="form-field">
          <span class="field-label">病历完成人：</span>
          <input v-model="formData.recordCompleter" class="field-value" />
        </div>
      </div>
    </div>

    <!-- 生命体征 -->
    <div class="form-section">
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">生命体征：</span>
        </div>
        <div class="form-field">
          <span class="field-label">BP：</span>
          <input v-model="formData.bloodPressure" class="field-value" placeholder="153/84mmHg" />
        </div>
        <div class="form-field">
          <span class="field-label">R：</span>
          <input v-model="formData.respiration" class="field-value" placeholder="23次/分" />
        </div>
        <div class="form-field">
          <span class="field-label">P：</span>
          <input v-model="formData.pulse" class="field-value" placeholder="104次/分" />
        </div>
        <div class="form-field">
          <span class="field-label">T：</span>
          <input v-model="formData.temperature" class="field-value" placeholder="36.5°C" />
        </div>
        <div class="form-field">
          <span class="field-label">SPO2：</span>
          <input v-model="formData.spo2" class="field-value" placeholder="97%" />
        </div>
        <div class="form-field">
          <span class="field-label">血糖：</span>
          <input v-model="formData.bloodSugar" class="field-value" placeholder="mmol/L" />
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">瞳孔：</span>
          <span class="field-label">左/右：</span>
          <input v-model="formData.pupilSize" class="field-value" placeholder="3/3 mm" />
        </div>
        <div class="form-field">
          <span class="field-label">对光反射：</span>
          <select v-model="formData.lightReflex" class="field-value">
            <option value="">请选择</option>
            <option value="存在">存在</option>
            <option value="迟钝">迟钝</option>
            <option value="消失">消失</option>
          </select>
        </div>
        <div class="form-field">
          <span class="field-label">呼吸状况：</span>
          <select v-model="formData.breathingStatus" class="field-value">
            <option value="">请选择</option>
            <option value="正常">正常</option>
            <option value="急促">急促</option>
            <option value="困难">困难</option>
          </select>
        </div>
        <div class="form-field">
          <span class="field-label">神志/意识：</span>
          <select v-model="formData.consciousness" class="field-value">
            <option value="">请选择</option>
            <option value="清醒">清醒</option>
            <option value="嗜睡">嗜睡</option>
            <option value="昏迷">昏迷</option>
          </select>
        </div>
      </div>
    </div>

    <!-- 主诉 -->
    <div class="form-section">
      <div class="form-row">
        <div class="form-field" style="width: 100%;">
          <span class="field-label">主诉：</span>
          <textarea v-model="formData.chiefComplaint" class="field-value text-area" 
                    placeholder="外伤右手下段右侧外伤，外科车辆碰撞外伤"></textarea>
        </div>
      </div>
    </div>

    <!-- 第二部分：院前急救医疗记录 -->
    <div class="form-subtitle">第二部分：院前急救医疗记录</div>
    
    <div class="form-section">
      <div class="form-row">
        <div class="form-field narrow-field">
          <span class="field-label">过敏史：</span>
          <select v-model="formData.allergyHistory" class="field-value">
            <option value="">请选择</option>
            <option value="无">无</option>
            <option value="有">有</option>
          </select>
        </div>
        <div class="form-field wide-field">
          <span class="field-label">既往史：</span>
          <textarea v-model="formData.pastHistory" class="field-value text-area"></textarea>
        </div>
      </div>
    </div>

    <!-- 红框区域 - 急救措施 -->
    <div class="red-box">
      <div class="form-row">
        <div class="form-field" style="width: 100%;">
          <span class="field-label">急救措施：</span>
        </div>
      </div>
      
      <!-- 左右分栏布局 -->
      <div class="form-row">
        <!-- 左侧栏 -->
        <div class="form-field" style="width: 50%; flex-direction: column; align-items: flex-start;">
          <!-- 急救科目 -->
          <div style="margin-bottom: 15px; width: 100%;">
            <div style="font-weight: bold; margin-bottom: 8px; border-bottom: 1px solid #333; padding-bottom: 3px;">
              急救科目：
            </div>
            <div class="checkbox-group" style="flex-direction: column; align-items: flex-start;">
              <label class="checkbox-item">
                <input type="checkbox" v-model="formData.emergencySubjects.bloodPressureMonitoring" />
                <span>血压监测</span>
              </label>
              <label class="checkbox-item">
                <input type="checkbox" v-model="formData.emergencySubjects.heartMonitoring" />
                <span>心电监护</span>
              </label>
              <label class="checkbox-item">
                <input type="checkbox" v-model="formData.emergencySubjects.oxygenTherapy" />
                <span>吸氧</span>
              </label>
              <label class="checkbox-item">
                <input type="checkbox" v-model="formData.emergencySubjects.ivAccess" />
                <span>建立静脉通路</span>
              </label>
            </div>
          </div>
          
          <!-- 后续检查 -->
          <div style="margin-bottom: 15px; width: 100%;">
            <div style="font-weight: bold; margin-bottom: 8px; border-bottom: 1px solid #333; padding-bottom: 3px;">
              后续检查：
            </div>
            <textarea v-model="formData.followUpExamination" 
                      style="width: 100%; min-height: 60px; border: 1px solid #ccc; padding: 5px; font-family: inherit; resize: vertical;"
                      placeholder="请填写后续检查内容"></textarea>
          </div>
        </div>
        
        <!-- 右侧栏 -->
        <div class="form-field" style="width: 50%; flex-direction: column; align-items: flex-start; border-left: 1px solid #333; padding-left: 10px;">
          <!-- 项目支持 -->
          <div style="margin-bottom: 15px; width: 100%;">
            <div style="font-weight: bold; margin-bottom: 8px; border-bottom: 1px solid #333; padding-bottom: 3px;">
              项目支持：
            </div>
            <div class="checkbox-group" style="flex-direction: column; align-items: flex-start;">
              <label class="checkbox-item">
                <input type="checkbox" v-model="formData.projectSupport.emergency" />
                <span>急诊科</span>
              </label>
              <label class="checkbox-item">
                <input type="checkbox" v-model="formData.projectSupport.orthopedics" />
                <span>骨科</span>
              </label>
              <label class="checkbox-item">
                <input type="checkbox" v-model="formData.projectSupport.cardiology" />
                <span>心内科</span>
              </label>
              <label class="checkbox-item">
                <input type="checkbox" v-model="formData.projectSupport.neurology" />
                <span>神经科</span>
              </label>
            </div>
          </div>
          
          <!-- 院内准备 -->
          <div style="margin-bottom: 15px; width: 100%;">
            <div style="font-weight: bold; margin-bottom: 8px; border-bottom: 1px solid #333; padding-bottom: 3px;">
              院内准备：
            </div>
            <textarea v-model="formData.hospitalPreparation" 
                      style="width: 100%; min-height: 60px; border: 1px solid #ccc; padding: 5px; font-family: inherit; resize: vertical;"
                      placeholder="请填写院内准备情况"></textarea>
          </div>
        </div>
      </div>
      
      <!-- 底部区域 -->
      <div class="form-row">
        <div class="form-field" style="width: 100%;">
          <div style="font-weight: bold; margin-bottom: 8px; border-bottom: 1px solid #333; padding-bottom: 3px;">
            现场检查：
          </div>
          <textarea v-model="formData.onSiteExamination" 
                    style="width: 100%; min-height: 40px; border: 1px solid #ccc; padding: 5px; font-family: inherit; resize: vertical;"
                    placeholder="左踝皮肤挫伤"></textarea>
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field" style="width: 100%;">
          <div style="font-weight: bold; margin-bottom: 8px; border-bottom: 1px solid #333; padding-bottom: 3px;">
            给药情况：
          </div>
          <textarea v-model="formData.medicationAdministered" 
                    style="width: 100%; min-height: 40px; border: 1px solid #ccc; padding: 5px; font-family: inherit; resize: vertical;"
                    placeholder="请填写用药情况"></textarea>
        </div>
      </div>
    </div>

    <!-- 第三部分：转归情况 -->
    <div class="form-subtitle">第三部分：转归情况</div>
    
    <div class="form-section">
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">转归去向：</span>
          <select v-model="formData.disposition" class="field-value">
            <option value="">请选择</option>
            <option value="住院">住院</option>
            <option value="门诊">门诊</option>
            <option value="转院">转院</option>
            <option value="死亡">死亡</option>
          </select>
        </div>
        <div class="form-field wide-field">
          <span class="field-label">急救效果：</span>
          <select v-model="formData.treatmentEffect" class="field-value">
            <option value="">请选择</option>
            <option value="有效">有效</option>
            <option value="无效">无效</option>
            <option value="好转">好转</option>
          </select>
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field wide-field">
          <span class="field-label">第四部分：交接情况</span>
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">BP：</span>
          <input v-model="formData.finalBP" class="field-value" placeholder="154/86 mmHg" />
        </div>
        <div class="form-field">
          <span class="field-label">R：</span>
          <input v-model="formData.finalR" class="field-value" placeholder="20 次/分" />
        </div>
        <div class="form-field">
          <span class="field-label">P：</span>
          <input v-model="formData.finalP" class="field-value" placeholder="102 次/分" />
        </div>
        <div class="form-field">
          <span class="field-label">T：</span>
          <input v-model="formData.finalT" class="field-value" placeholder="36.4°C" />
        </div>
        <div class="form-field">
          <span class="field-label">SPO2：</span>
          <input v-model="formData.finalSPO2" class="field-value" placeholder="97%" />
        </div>
        <div class="form-field">
          <span class="field-label">血糖：</span>
          <input v-model="formData.finalBloodSugar" class="field-value" placeholder="mmol/L" />
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">对光反射：</span>
          <select v-model="formData.finalLightReflex" class="field-value">
            <option value="">请选择</option>
            <option value="存在">存在</option>
            <option value="迟钝">迟钝</option>
            <option value="消失">消失</option>
          </select>
        </div>
        <div class="form-field">
          <span class="field-label">神志/意识：</span>
          <select v-model="formData.finalConsciousness" class="field-value">
            <option value="">请选择</option>
            <option value="清醒">清醒</option>
            <option value="嗜睡">嗜睡</option>
            <option value="昏迷">昏迷</option>
          </select>
        </div>
      </div>
      
      <div class="form-row">
        <div class="form-field">
          <span class="field-label">呼吸状况：</span>
          <select v-model="formData.finalBreathing" class="field-value">
            <option value="">请选择</option>
            <option value="正常">正常</option>
            <option value="急促">急促</option>
            <option value="困难">困难</option>
          </select>
        </div>
        <div class="form-field wide-field">
          <span class="field-label">其他：</span>
          <textarea v-model="formData.otherNotes" class="field-value text-area"></textarea>
        </div>
      </div>
    </div>

    <!-- 签名区域 -->
    <div class="signature-section">
      <div class="signature-field">
        <div class="signature-label">出诊医师</div>
        <div class="signature-line"></div>
        <div>签名</div>
      </div>
      <div class="signature-field">
        <div class="signature-label">出诊护士</div>
        <div class="signature-line"></div>
        <div>签名</div>
      </div>
      <div class="signature-field">
        <div class="signature-label">接诊医生护士</div>
        <div class="signature-line"></div>
        <div>交接时间：2024-07-02 14:39:11</div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from 'vue'

const formData = reactive({
  // 基本信息
  name: '朱红',
  gender: '男',
  age: 39,
  idNumber: '511241986051026510',
  dispatchAddress: '市中区某某路某某号楼下方向500m',
  contactPhone: '13182252764',
  callTime: '2024-07-02T13:35:56',
  departureTime: '2024-07-02T13:53:59',
  arrivalTime: '2024-07-02T15:01:00',
  leaveTime: '',
  hospitalArrivalTime: '2024-07-02T14:22:43',
  recordCompleter: '病人',
  
  // 生命体征
  bloodPressure: '153/84mmHg',
  respiration: '23次/分',
  pulse: '104次/分',
  temperature: '36.5°C',
  spo2: '97%',
  bloodSugar: 'mmol/L',
  pupilSize: '3/3 mm',
  lightReflex: '存在',
  breathingStatus: '正常',
  consciousness: '清醒',
  
  // 主诉
  chiefComplaint: '外伤右手下段右侧外伤，外科车辆碰撞外伤',
  
  // 病史
  allergyHistory: '无',
  pastHistory: '',
  
  // 急救科目
  emergencySubjects: {
    bloodPressureMonitoring: false,
    heartMonitoring: false,
    oxygenTherapy: false,
    ivAccess: false
  },
  
  // 项目支持
  projectSupport: {
    emergency: false,
    orthopedics: false,
    cardiology: false,
    neurology: false
  },
  
  // 检查和处理
  followUpExamination: '',
  onSiteExamination: '左踝皮肤挫伤',
  medicationAdministered: '',
  hospitalPreparation: '',
  
  // 转归情况
  disposition: '住院',
  treatmentEffect: '有效',
  
  // 最终生命体征
  finalBP: '154/86 mmHg',
  finalR: '20 次/分',
  finalP: '102 次/分',
  finalT: '36.4°C',
  finalSPO2: '97%',
  finalBloodSugar: 'mmol/L',
  finalLightReflex: '存在',
  finalConsciousness: '清醒',
  finalBreathing: '正常',
  otherNotes: ''
})
</script>