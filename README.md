# 工厂QC检验记录 + 中英双语翻译工具
class QCInspector:
    def init(self):
        # 中英对照常用词
        self.word_map = {
            "合格": "Pass",
            "不合格": "Fail",
            "检验": "Inspection",
            "产品": "Product",
            "批次": "Batch",
            "数量": "Quantity",
            "日期": "Date",
            "外观": "Appearance",
            "尺寸": "Size",
            "重量": "Weight",
            "通过": "Pass",
            "返工": "Rework",
            "报废": "Scrap"
        }

    # 翻译：中 → 英
    def translate_cn_to_en(self, word):
        return self.word_map.get(word, "Unknown")

    # 翻译：英 → 中
    def translate_en_to_cn(self, word):
        reverse_map = {v: k for k, v in self.word_map.items()}
        return reverse_map.get(word, "Unknown")

    # 记录一条QC检验结果
    def add_record(self, batch_no, product_name, qty, result, remark=""):
        record = {
            "batch": batch_no,
            "product": product_name,
            "qty": qty,
            "result": result,
            "remark": remark
        }
        print("✅ QC记录已添加：")
        print(f"批次：{batch_no} | 产品：{product_name} | 数量：{qty} | 结果：{result} | 备注：{remark}")
        return record

# 示例使用
if name == "main":
    qc = QCInspector()

    # 翻译
    print("中 → 英：合格 =", qc.translate_cn_to_en("合格"))
    print("英 → 中：Fail =", qc.translate_en_to_cn("Fail"))

    # 添加检验记录
    qc.add_record("B20260425", "轮胎", 500, "合格", "外观正常")
    qc.add_record("B20260425-02", "轮胎", 20, "不合格", "尺寸偏差")
